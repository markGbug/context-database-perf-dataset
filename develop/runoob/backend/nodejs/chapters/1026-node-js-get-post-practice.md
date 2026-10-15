# Node.js：Node.js GET/POST请求

- 来源：[Node.js GET/POST请求](https://www.runoob.com/nodejs/node-js-get-post.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：练习笔记
- 章节序号：1026

## 本章内容

在很多场景中，我们的服务器都需要跟用户的浏览器打交道，如表单提交。

表单提交到服务器一般都使用 GET/POST 请求。

本章节我们将为大家介绍 Node.js GET/POST请求。


## 获取GET请求内容

由于 GET 请求直接被嵌入在路径中，URL 是完整的请求路径，包括了 ? 后面的部分，因此你可以手动解析后面的内容作为 GET 请求的参数。

node.js 中 可以使用 URL 构造函数解析请求的 URL。

URL 对象是 Node.js 中用于解析和操作 URL 的一种标准工具。它提供了方便的接口来访问和修改 URL 的各个组成部分，如协议、主机名、路径、查询参数等。


## 实例

```javascript
const http = require('http');
const util = require('util');

http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain; charset=utf-8' });

    // 使用 URL 构造函数解析请求的 URL
    const myUrl = new URL(req.url, `http://${req.headers.host}`);

    // 输出 URL 的各个部分
    res.end(util.inspect({
        href: myUrl.href,
        origin: myUrl.origin,
        protocol: myUrl.protocol,
        host: myUrl.host,
        hostname: myUrl.hostname,
        port: myUrl.port,
        pathname: myUrl.pathname,
        search: myUrl.search,
        searchParams: Object.fromEntries(myUrl.searchParams) // 将 searchParams 转为普通对象
    }));
}).listen(3000);

console.log("Server is running at http://localhost:3000");
```

在浏览器中访问 http://localhost:3000/user?name=菜鸟教程&url=www.runoob.com 然后查看返回结果:


### 获取 URL 的参数

我们可以使用 url.parse 方法来解析 URL 中的参数，代码如下：


## 实例

```javascript
const http = require('http');

http.createServer((req, res) => {
    res.writeHead(200, { 'Content-Type': 'text/plain; charset=utf-8' });

    // 使用 URL 构造函数解析请求 URL
    const myUrl = new URL(req.url, `http://${req.headers.host}`);

    // 获取查询参数
    const name = myUrl.searchParams.get("name");
    const siteUrl = myUrl.searchParams.get("url");

    res.write("网站名：" + (name || "未提供"));
    res.write("\n");
    res.write("网站 URL：" + (siteUrl || "未提供"));
    res.end();

}).listen(3000);

console.log("Server is running at http://localhost:3000");
```

在浏览器中访问 http://localhost:3000/user?name=菜鸟教程&url=www.runoob.com 然后查看返回结果:


### URL 对象

以下是 URL 对象的属性和方法：


## 实例


## 获取 POST 请求内容

在 Node.js 中，处理 POST 请求通常需要通过 http 模块来接收请求体中的数据。POST 请求数据不像 GET 请求那样包含在 URL 中，而是作为请求体发送。因此，在 Node.js 中接收 POST 数据时，需要监听并处理 request 对象的 data 和 end 事件。

- 监听 data 事件：当数据块到达服务器时，data 事件触发，数据块作为回调的参数传递。
- 监听 end 事件：当整个请求体接收完毕时，end 事件触发，这时可以对完整的 POST 数据进行处理。


## 实例

代码说明：

- 检测请求方法：通过 req.method === 'POST' 来判断请求类型是否为 POST。
- 接收数据：在 req.on('data') 事件中累加数据块，形成完整的数据体。
- 完成接收：在 req.on('end') 事件中处理完整的 POST 数据。
- 响应客户端：完成数据接收和处理后，向客户端发送响应。

你可以使用 curl 命令来测试 POST 请求：

```text
curl -X POST -d "name=example&age=25" http://localhost:3000
```


### 处理 JSON 数据

如果 POST 请求发送的是 JSON 数据，可以在 req.on('end') 中将接收的数据解析为对象：

```javascript
req.on('end', () => {
    const parsedData = JSON.parse(body); // 将 JSON 字符串解析为对象
    console.log('Received JSON data:', parsedData);
    res.end('JSON data received successfully!');
});
```


### querystring 模块


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Node.js GET/POST请求` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
