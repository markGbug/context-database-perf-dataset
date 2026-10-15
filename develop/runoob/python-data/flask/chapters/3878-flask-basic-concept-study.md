# Flask：Flask 基本概念

- 来源：[Flask 基本概念](https://www.runoob.com/flask/flask-basic-concept.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：学习笔记
- 章节序号：3878

## 本章内容

上一个章节我们已经学会了如何创建第一个 Flask 应用，本章节我们将来详细了解 Flask 的一些基本概念。

了解 Flask 的基本概念对于开发高效的 Web 应用非常重要。

以下是 Flask 的主要基本概念的详细解析：

- 路由：路由是 URL 到 Python 函数的映射。Flask 允许你定义路由，这样当特定的 URL 被访问时，就会调用相应的函数。
- 视图函数：视图函数是处理请求并返回响应的 Python 函数。它们通常接收请求对象作为参数，并返回响应对象。
- 请求对象：请求对象包含了客户端发送的请求信息，如请求方法、URL、请求头、表单数据等。
- 响应对象：响应对象包含了发送给客户端的响应信息，如状态码、响应头、响应体等。
- 模板：Flask 使用 Jinja2 模板引擎来渲染 HTML 模板。模板允许你将 Python 代码嵌入到 HTML 中，从而动态生成网页。
- 应用工厂：应用工厂是一个 Python 函数，它创建并返回一个 Flask 应用实例。这允许你配置和初始化你的应用，并且可以创建多个应用实例。
- 配置对象：Flask 应用有一个配置对象，你可以使用它来设置各种配置选项，如数据库连接字符串、调试模式等。
- 蓝图：蓝图是 Flask 中的一个组织代码的方式，它允许你将相关的视图函数、模板和静态文件组织在一起，并且可以在多个应用中重用。
- 静态文件：静态文件是不会被服务器端执行的文件，如 CSS、JavaScript 和图片文件。Flask 提供了一个简单的方法来服务这些文件。
- 扩展：Flask 有许多扩展，可以添加额外的功能，如数据库集成、表单验证、用户认证等。
- 会话：Flask 使用客户端会话来存储用户信息，这允许你在用户浏览你的应用时记住他们的状态。
- 错误处理：Flask 允许你定义错误处理函数，当特定的错误发生时，这些函数会被调用。


### 1. 路由 (Routing)

路由是 URL 到 Python 函数的映射。Flask 允许你定义路由，使得当用户访问特定 URL 时，Flask 会调用对应的视图函数来处理请求。


## 实例

- @app.route('/')：将根 URL / 映射到 home 函数。
- @app.route('/about')：将 /about URL 映射到 about 函数。


### 2. 视图函数 (View Functions)

视图函数是处理请求并返回响应的 Python 函数。它们通常接收请求对象作为参数，并返回响应对象，或者直接返回字符串、HTML 等内容。


## 实例

greet 函数接收 URL 中的 name 参数，并返回一个字符串响应。


### 3. 请求对象 (Request Object)

请求对象包含了客户端发送的请求信息，包括请求方法、URL、请求头、表单数据等。Flask 提供了 request 对象来访问这些信息。


## 实例

request.form.get('username')：获取 POST 请求中表单数据的 username 字段。


### 4. 响应对象 (Response Object)

响应对象包含了发送给客户端的响应信息，包括状态码、响应头和响应体。Flask 默认会将字符串、HTML 直接作为响应体。


## 实例

make_response：创建一个自定义响应对象，并设置响应头 X-Custom-Header。


### 5. 模板 (Templates)

Flask 使用 Jinja2 模板引擎来渲染 HTML 模板。模板允许你将 Python 代码嵌入到 HTML 中，从而动态生成网页内容。


## 实例

模板文件 (templates/hello.html)：


## 实例


### 6. 应用工厂 (Application Factory)

应用工厂是一个 Python 函数，用于创建和配置 Flask 应用实例。这种方法允许你创建多个应用实例，或者在不同配置下初始化应用。


## 实例

create_app 函数创建一个 Flask 应用实例，并从配置对象中加载配置。


### 7. 配置对象 (Configuration Objects)

配置对象用于设置应用的各种配置选项，如数据库连接字符串、调试模式等。可以通过直接设置或加载配置文件来配置 Flask 应用。


## 实例

app.config.from_object(Config)：将 Config 类中的配置项加载到应用配置中。


### 8. 蓝图 (Blueprints)

蓝图是 Flask 中的组织代码的方式。它允许你将相关的视图函数、模板和静态文件组织在一起，并且可以在多个应用中重用。


## 实例

注册蓝图 (app/__init__.py)：


## 实例


### 9. 静态文件 (Static Files)

静态文件是不会被服务器端执行的文件，如 CSS、JavaScript 和图片文件。Flask 提供了一个简单的方法来服务这些文件。

访问静态文件示例：

```java
<link rel="stylesheet" type="text/css" href="{{ url_for('static', filename='style.css') }}">
```

静态文件目录：将静态文件放在 static 文件夹中，Flask 会自动提供服务。


### 10. 扩展 (Extensions)

Flask 有许多扩展，可以添加额外的功能，如数据库集成、表单验证、用户认证等。这些扩展提供了更高级的功能和第三方集成。


## 实例

SQLAlchemy：用于数据库集成的扩展。


### 11. 会话 (Sessions)

Flask 使用客户端会话来存储用户信息，以便在用户浏览应用时记住他们的状态。会话数据存储在客户端的 cookie 中，并在服务器端进行签名和加密。


## 实例

session 对象用于存取会话数据。

你可以使用 Python 内置的 secrets 模块生成一个强随机性的密钥。

```text
python3 -c 'import secrets; print(secrets.token_hex())'
```


### 12. 错误处理 (Error Handling)

Flask 允许你定义错误处理函数，当特定的错误发生时，这些函数会被调用。可以自定义错误页面或处理逻辑。


## 后续章节

- 实例

## 复习重点

- 能说明 `Flask 基本概念` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
