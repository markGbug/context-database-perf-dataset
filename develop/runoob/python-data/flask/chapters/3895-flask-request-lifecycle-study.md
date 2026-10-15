# Flask：Flask 请求生命周期

- 来源：[Flask 请求生命周期](https://www.runoob.com/flask/flask-request-lifecycle.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3895

## 本章内容

理解 Flask 请求的完整生命周期，是写好 Flask 应用的关键。

本章从源码层面拆解一个 HTTP 请求从进入服务器到返回响应的全过程，帮你建立清晰的执行模型。


## 什么是请求生命周期

请求生命周期（Request Lifecycle）指的是一个 HTTP 请求在 Flask 内部经历的完整处理过程。

它包含以下阶段：接收请求 → 创建上下文 → 预处理 → 路由分发 → 视图执行 → 响应构建 → 清理上下文 → 返回响应。

了解这个过程，你就能正确回答以下问题：

- g 对象的数据什么时候可用？什么时候被清理？
- before_request 和 after_request 的执行顺序是什么？
- 异常发生时会依次经过哪些处理环节？
- 为什么在视图函数外使用 request 会报错？


## 完整流程图

下图展示了 Flask 从接收请求到返回响应的完整调用链：


## 分步详解


### 第一阶段：WSGI 入口

当 HTTP 请求到达服务器时，WSGI 服务器（如 Gunicorn、Werkzeug 开发服务器）会调用 Flask 应用实例。

Flask 实现了 __call__ 方法，使其成为一个合法的 WSGI 应用：


## 实例

Flask 把入口点设计为调用 wsgi_app 方法，而不是直接在 __call__ 里写逻辑。这样你可以通过替换 app.wsgi_app 来插入中间件，而不影响对 app 实例本身的调用。


### 第二阶段：创建上下文

request_context(environ) 根据 WSGI 环境变量创建一个 AppContext 对象。

这个对象包含了当前请求的所有信息，当它被推入栈中后，request、session、g、current_app 这些全局代理才开始指向当前请求的数据。


## 实例

初学者最容易犯的错误就是在模块级别直接访问 request。记住：request 只有在请求上下文中才存在。你只能在视图函数内部（或它调用的函数里）访问它。


### 第三阶段：preprocess_request（预处理）

上下文就绪后，full_dispatch_request 首先调用 preprocess_request。

这个阶段会执行所有用 @app.before_request 注册的函数。

如果任意一个 before_request 函数返回了非 None 的值，Flask 会把它当作最终响应，跳过后续的视图函数执行。


## 实例


### 第四阶段：dispatch_request（路由分发）

预处理完成后，Flask 进入核心的分发阶段：

- 匹配 URL 到对应的路由规则（Rule）
- 提取 URL 中的变量参数（view_args）
- 调用对应的视图函数，传入提取的参数


## 实例

匹配失败时会抛出 RoutingException，最终由错误处理器捕获并返回 404。


### 第五阶段：视图函数执行

这是你编写业务逻辑的地方。Flask 调用你的视图函数并获取返回值。

返回值可以是多种类型——字符串、字典、元组、Response 对象——这些都会在下一阶段被统一处理。


### 第六阶段：finalize_request（响应构建）

视图函数执行完毕后，finalize_request 负责将返回值转换为标准的 Response 对象：


## 实例

make_response 的转换规则：


### 第七阶段：after_request 钩子

process_response 在执行 make_response 之后，依次调用所有 @app.after_request 注册的函数。

每个 after_request 函数接收并返回 Response 对象，可以修改响应头、添加 Cookie 等。


## 实例


### 第八阶段：上下文清理

响应发送后，finally 块中的 ctx.pop() 执行上下文清理：

- 调用所有 teardown_request 注册的函数（无论请求成功或失败都会执行）
- 调用所有 teardown_appcontext 注册的函数
- 发送 request_tearing_down 和 appcontext_tearing_down 信号
- 释放 g 对象中存储的所有数据


## 实例


## 异常处理流程

当视图函数抛出异常时，Flask 有一条专门的异常处理路径：

- full_dispatch_request 捕获异常
- 调用 handle_user_exception 判断异常类型
- HTTP 异常（如 abort(404)）→ 查找对应的 errorhandler
- 普通异常 → 查找异常类的 errorhandler
- 找不到处理器 → 调用 handle_exception，返回 500 错误
- 无论异常与否，最终都会经过 finalize_request 构建响应

异常路径中的关键点：after_request 钩子对错误响应也会执行（从 Flask 1.1 开始），但 before_request 返回的非 None 值会短路整个流程，后面的视图函数和钩子都不会执行。


## 钩子函数速查表


## 信号事件

Flask 使用 blinker 库在关键节点发送信号：


## 实例


## 关键要点总结

核心规则：一个完整的请求生命周期中，before_request → 视图函数 → after_request → teardown 这四个节点一定会按顺序执行（teardown 始终执行，无论前三个是否出错）。

理解请求生命周期后，你在写 Flask 应用时就知道：认证逻辑放 before_request，业务逻辑放视图函数，响应头修改放 after_request，资源清理放 teardown。


## 复习重点

- 能说明 `Flask 请求生命周期` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
