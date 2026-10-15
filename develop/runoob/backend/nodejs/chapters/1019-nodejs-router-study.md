# Node.js：Node.js 路由

- 来源：[Node.js 路由](https://www.runoob.com/nodejs/nodejs-router.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：学习笔记
- 章节序号：1019

## 本章内容

在 Node.js 中，路由是处理 HTTP 请求的关键部分，它决定了如何根据不同的 URL 和 HTTP 方法（如 GET、POST、PUT、DELETE 等）来分发请求。

路由通常用于构建 Web 应用程序，特别是 RESTful API。

Node.js 本身并没有内置的路由机制，但可以通过中间件库（如 Express）来实现。

路由通常涉及以下几个方面：

- URL 匹配：根据请求的 URL 来匹配路由规则。
- HTTP 方法匹配：根据请求的 HTTP 方法（GET、POST、PUT、DELETE 等）来匹配路由规则。
- 请求处理：一旦匹配到合适的路由规则，就调用相应的处理函数来处理请求。

Node.js 中，我们可以通过 http 模块创建一个简单的路由，如下实例：


## 实例

浏览器访问 http://localhost:3000 显示如下：

浏览器访问 http://localhost:3000/about 显示如下：

如果访问其他 URL 地址，则会直接显示 404 Not Found。

更多 HTTP 请求可以参考：HTTP 教程。


## 请求参数

一个完整 URL 的 http://localhost:8888/start?foo=bar&hello=world 包含主机、路径和查询字符串。

为了解析这些数据，我们可以使用 URL 对象和 querystring 模块。

```javascript
const myUrl = new URL("http://localhost:8888/start?foo=bar&hello=world");

// 提取路径名
console.log(myUrl.pathname); // 输出: /start

// 提取查询参数
console.log(myUrl.searchParams.get("foo"));   // 输出: bar
console.log(myUrl.searchParams.get("hello")); // 输出: world
```

```text
myUrl.pathname
          |
          |
        -----
http://localhost:8888/start?foo=bar&hello=world
                                ---       -----
                                 |          |
                                 |          |
           myUrl.searchParams.get("foo")    |
                                            |
                                     myUrl.searchParams.get("hello")
```

当然我们也可以用 querystring 模块来解析 POST 请求体中的参数，相关内容后面的 Node.js GET/POST请求 会介绍。

我们需要的所有请求数据都会包含在 request 对象中，该对象作为 onRequest() 回调函数的第一个参数传递。


## 复习重点

- 能说明 `Node.js 路由` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
