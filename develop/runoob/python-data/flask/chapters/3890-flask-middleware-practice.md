# Flask：Flask 中间件和扩展

- 来源：[Flask 中间件和扩展](https://www.runoob.com/flask/flask-middleware.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3890

## 本章内容

在 Flask 中，中间件和扩展是增强和扩展应用功能的两个关键机制。

通过中间件和扩展，你可以大大增强 Flask 应用的功能和灵活性，使得应用能够满足各种复杂的需求。

下面详细介绍这两者的概念和如何使用它们。

Flask 中间件：

- 使用请求钩子在请求处理的不同阶段插入代码。
- 创建自定义中间件类来处理请求和响应。

Flask 扩展：

- 使用现有的扩展（如 Flask-SQLAlchemy、Flask-WTF）来添加功能。
- 创建自定义扩展来满足特定需求。


## 1. Flask 中间件

Flask 的中间件（middleware）是对请求和响应进行处理的钩子，通常用于在请求到达视图函数之前或在响应发送到客户端之前执行一些操作。中间件可以用于日志记录、请求修改、响应修改等。


### 1.1 请求钩子

请求钩子允许你在处理请求的不同阶段插入代码，Flask 提供了几种钩子来处理请求生命周期的不同阶段：

- before_request：在每个请求处理之前执行。
- after_request：在每个请求处理之后执行。
- teardown_request：请求处理结束后，无论是否发生异常都会执行。
- before_first_request：仅在应用第一次处理请求之前执行。

app.py 文件代码：


## 实例

- @app.before_request：在每个请求处理之前打印 "Before request"。
- @app.after_request：在每个请求处理之后打印 "After request"。
- @app.teardown_request：在每个请求处理后（无论是否发生异常）打印 "Teardown request"。


### 1.2 自定义中间件

Flask 还允许你创建自定义中间件类，这些中间件类可以在请求和响应处理的各个阶段进行操作。

middleware.py 文件代码：


## 实例

app.py 文件代码：


## 实例

CustomMiddleware：自定义中间件类，添加一个自定义响应头。


## 2. Flask 扩展

Flask 扩展是用于为 Flask 应用添加功能的插件。Flask 的扩展可以集成第三方库，提供例如数据库集成、表单处理、用户认证等功能。


### 2.1 常见的 Flask 扩展

- Flask-SQLAlchemy：集成 SQLAlchemy ORM，使数据库操作更方便。
- Flask-WTF：集成 WTForms 表单库，简化表单处理。
- Flask-Login：提供用户会话管理和用户认证功能。
- Flask-Migrate：用于数据库迁移的扩展，基于 Alembic。
- Flask-Mail：用于发送电子邮件。


### 2.2 安装和使用 Flask 扩展

以 Flask-SQLAlchemy 为例，安装：

```text
pip install flask-sqlalchemy
```

配置和使用，app.py 文件代码：


## 实例

SQLAlchemy 扩展集成了 SQLAlchemy，使得你可以轻松地定义模型并与数据库交互。


### 2.3 创建自定义扩展

如果现有的扩展不能满足你的需求，你可以创建自己的扩展。创建自定义扩展通常涉及到定义一个类，提供初始化配置和相关功能。

myextension.py 文件代码；


## 实例

app.py 文件代码：


## 实例

MyExtension：自定义扩展，添加了一个自定义响应头。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask 中间件和扩展` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
