# FastAPI：FastAPI 错误处理

- 来源：[FastAPI 错误处理](https://www.runoob.com/fastapi/fastapi-error-handling.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：练习笔记
- 章节序号：3857

## 本章内容

在 API 开发中，需要向客户端返回错误信息。FastAPI 提供了 HTTPException 来抛出 HTTP 错误，也支持自定义异常处理器来处理更复杂的错误场景。


## 使用 HTTPException

当需要返回错误响应时，抛出 HTTPException：


## 实例

访问 http://127.0.0.1:8000/items/42 时，返回：

```text
{
    "detail": "Item not found"
}
```

HTTP 状态码为 404。

注意这里使用的是 raise 而不是 return。HTTPException 是一个异常，抛出后 FastAPI 会捕获它并返回对应的 HTTP 错误响应。这与 Python 的异常处理机制一致。


## HTTPException 参数


## 自定义错误详情

detail 参数可以是任意类型，不局限于字符串：


## 实例


## 添加自定义响应头

某些场景下需要在错误响应中添加自定义响应头：


## 实例

在需要限制客户端请求频率（限流）的场景中，可以在错误响应头中添加 Retry-After 头，告诉客户端何时可以重试。


## 自定义异常处理器

你可以为自定义异常或内置异常注册处理器，统一处理错误响应格式：


## 实例


## 覆盖默认异常处理器

FastAPI 有默认的异常处理器，你可以覆盖它们来自定义错误响应格式：


## 实例

RequestValidationError 是 FastAPI 在请求数据校验失败时抛出的异常。覆盖它的处理器可以自定义校验错误的响应格式。


## 重定向

使用 RedirectResponse 实现重定向：


## 实例


## 自定义响应头和状态码

使用 JSONResponse 自定义响应头和状态码：


## 实例


## 小结

- 使用 raise HTTPException 返回 HTTP 错误响应
- detail 参数可以是任意类型（字符串、字典、列表等）
- 使用 @app.exception_handler 注册自定义异常处理器
- 可以覆盖 FastAPI 默认的异常处理器来统一错误格式
- 使用 RedirectResponse 实现重定向


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `FastAPI 错误处理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
