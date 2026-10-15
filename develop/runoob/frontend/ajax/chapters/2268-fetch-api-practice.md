# AJAX：Fetch API

- 来源：[Fetch API](https://www.runoob.com/ajax/fetch-api.html)
- 分类：前端开发
- 技术：AJAX
- 笔记类型：练习笔记
- 章节序号：2268

## 本章内容

Fetch API 是一种现代的、功能强大的网络请求工具，它允许你通过 JavaScript 异步地请求资源，而不需要使用传统的 XMLHttpRequest 对象。

Fetch API 可以简洁地发起 HTTP 请求，并处理服务器的响应。

Fetch API 基于 Promise 设计，使得异步操作更加简洁和易于理解。

Fetch 优点：

- 基于 Promises，代码更加简洁和易读。
- 更好的错误处理机制：只在网络错误（如无法连接服务器）时返回 catch，而非状态码错误。
- 支持多种数据格式（JSON、文本、二进制等）。
- 可以处理跨域请求，通过 CORS 机制配置。


### fetch 的基本用法

fetch 的语法相当简洁，最基本的形式是：

```javascript
fetch(url)
  .then(response => response.json()) // 解析 JSON 数据
  .then(data => console.log(data))   // 处理数据
  .catch(error => console.error('Error:', error)); // 错误处理
```

参数：

- url：要发送请求的目标 URL。
- options（可选）：可以指定请求方法（GET、POST 等）、请求头、请求体等内容。


### 返回值

返回一个 Promise 对象，Promise 在请求成功时返回 Response 对象，在请求失败时被拒绝。


## 使用 Fetch

1、基本 GET 请求：


## 实例

在这个例子中，fetch 默认执行 GET 请求，返回的 response 是一个 Response 对象，通过调用 .json() 方法来解析 JSON 数据。

2、发送 POST 请求：


## 实例

这里，我们通过设置 method 为 'POST' 来发送 POST 请求，并在请求体 body 中发送 JSON 格式的数据。

3、处理响应状态：


## 实例

在处理响应时，我们首先检查响应状态是否成功（response.ok），如果不成功则抛出错误。

4、发送带凭据的请求：


## 实例

使用 credentials: 'include' 可以在跨域请求中发送 cookies。

5、使用 Request 和 Response 对象：


## 实例

你可以创建 Request 对象来定制请求，fetch 会返回一个 Response 对象，你可以用它来获取不同类型的响应体，如 blob、text、json 等。

6、错误处理：


## 实例

在链式调用中，任何地方抛出的错误都会被 .catch() 捕获。

7、设置请求头

可以通过 headers 属性为请求添加自定义的 HTTP 头信息，例如 Content-Type、Authorization 等。


## 实例

8、处理非 200 的响应状态

fetch 不会自动将 HTTP 错误状态（如 404 或 500）作为拒绝的 Promise，仍然需要检查响应状态。


## 实例

9、发送表单数据

可以使用 FormData 对象将表单数据发送给服务器：


## 实例

10、跨域请求

如果需要进行跨域请求，可以在服务器端设置 CORS（Cross-Origin Resource Sharing）。在前端，也可以通过 credentials 选项来指定是否发送 cookies 等凭据。


## 实例


## Fetch 与 PHP

在 PHP 中使用 AJAX 请求与在其他后端语言中使用 AJAX 没有本质区别。PHP 脚本会在服务器端接收请求、处理数据，然后返回响应。

客户端 JavaScript 代码使用 Fetch API 发送请求和处理响应。

例如，如果你有一个 PHP 文件 server.php，它接收一个 GET 请求并返回一些数据，你可以这样使用 Fetch：


## 实例

在 PHP 端，你将解析请求参数并返回响应：


## 实例

这样，你就可以在客户端使用 Fetch API 与 PHP 后端进行通信了。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Fetch API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
