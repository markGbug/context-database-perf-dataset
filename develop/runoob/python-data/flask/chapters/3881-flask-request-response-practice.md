# Flask：Flask 请求与响应

- 来源：[Flask 请求与响应](https://www.runoob.com/flask/flask-request-response.html)
- 分类：Python / 数据科学
- 技术：Flask
- 笔记类型：练习笔记
- 章节序号：3881

## 本章内容

Web 应用的核心是「接收请求，返回响应」，本章全面讲解 Flask 中如何读取请求数据和构造各种类型的响应。

所有示例都可以在开发服务器中直接运行验证。


## 请求对象——request

Flask 通过全局代理对象 request 提供所有请求信息。

虽然它是「全局」对象，但 Flask 内部通过线程隔离机制确保每个请求获取的是自己的数据。


## 实例

访问 http://127.0.0.1:5000/debug?foo=bar 即可看到请求的详细信息。


## 获取查询参数——request.args

URL 中 ? 后面的参数称为查询参数（Query String）。

使用 request.args 读取，它像一个字典：


## 实例

推荐使用 .get() 方法而不是直接下标访问 request.args["key"]，因为后者在 key 不存在时会抛出 KeyError，导致返回 400 错误页面。


## 获取表单数据——request.form

处理 POST 请求提交的表单数据，使用 request.form：


## 实例

注意：处理表单的 HTML 页面中，<form> 必须设置 method="post"，否则数据会通过 URL 的查询字符串发送（GET 方式），敏感信息会暴露在 URL 中。


## 获取 JSON 数据——request.json

现代 Web 开发中，JSON 是最常见的数据格式。

当客户端发送 Content-Type: application/json 的请求时，使用 request.json 获取解析后的数据：


## 实例

可以用 curl 或 Postman 测试：

```text
$ curl -X POST http://127.0.0.1:5000/api/user \
  -H "Content-Type: application/json" \
  -d '{"name": "runoob", "email": "test@runoob.com"}'
{
  "message": "用户创建成功",
  "name": "runoob",
  "email": "test@runoob.com"
}
```


## 文件上传

处理上传的文件使用 request.files，配合 Werkzeug 提供的 secure_filename() 确保文件名安全：


## 实例

表单如果有文件上传字段，<form> 标签必须设置 enctype="multipart/form-data"，否则文件数据不会被浏览器发送。


## 响应类型完全指南

视图函数可以返回多种类型的数据，Flask 会自动将它们转换为合适的 HTTP 响应。

理解这个转换规则是掌握 Flask 的关键。


### 返回字符串

返回的字符串作为 HTML 响应体，状态码默认 200，Content-Type 为 text/html。


### 返回字典或列表（JSON）

自动调用 jsonify() 转换为 JSON 响应，Content-Type 为 application/json。


## 实例


### 返回元组——控制状态码和响应头

元组格式非常实用，有三种形式：


## 实例


## 重定向

使用 redirect() 函数将用户引导到另一个 URL：


## 实例

默认重定向状态码为 303 See Other，适用于表单提交后重定向（PRG 模式）。

对于永久迁移场景，应使用 code=301。


## 终止请求——abort

使用 abort() 立即终止当前请求并返回 HTTP 错误：


## 实例


## make_response——手动控制响应

当需要手动设置 Cookie 或自定义响应头时，使用 make_response()：


## 实例


## request 常用属性速查表


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Flask 请求与响应` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
