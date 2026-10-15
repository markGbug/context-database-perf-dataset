# Electron：Electron 网络与外部通信

- 来源：[Electron 网络与外部通信](https://www.runoob.com/electron/electron-network.html)
- 分类：后端开发
- 技术：Electron
- 笔记类型：练习笔记
- 章节序号：0833

## 本章内容

Electron 应用不仅可以操作本地资源，也可以与外部网络服务进行交互。 无论是发起 HTTP 请求、建立实时 WebSocket 连接，还是使用 Node.js 的原生 net 模块，你都可以像在浏览器或服务器上一样进行网络通信。


## HTTP 请求

Electron 同时支持 浏览器 API（fetch） 和 第三方库（axios），并且可以处理跨域与认证问题。


### fetch API 使用

fetch 是现代浏览器与 Node.js（18+）内置的网络请求接口。 它支持 Promise，语法简洁，适合常规数据请求。


## 实例

参数说明：

- fetch(url, options)：发起请求；
- options.method：请求方式（GET、POST、PUT、DELETE）；
- options.headers：设置请求头；
- options.body：请求体，POST 时常用。

POST 示例：

```text
fetch('https://api.example.com/login', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({ username: 'admin', password: '123456' })
});
```


### axios 集成

axios 是一个功能强大的 HTTP 客户端，支持拦截器、超时、并发等特性，常用于 Electron 应用中与后端 API 通信。

安装：

```text
npm install axios
```

使用示例：

```javascript
const axios = require('axios');

// GET 请求
axios.get('https://jsonplaceholder.typicode.com/users')
  .then(res => console.log(res.data))
  .catch(err => console.error(err));

// POST 请求
axios.post('https://api.example.com/data', { name: 'Tom' })
  .then(res => console.log('上传成功', res.data))
  .catch(err => console.error('上传失败', err));
```

参数说明：

- axios.get(url, config)：发起 GET 请求；
- axios.post(url, data, config)：发起 POST 请求；
- config.timeout：设置超时时间；
- config.headers：自定义请求头。


### 处理跨域问题

在 Electron 中，因为运行在桌面环境，默认不存在浏览器的 CORS 限制。 但如果前端页面通过 BrowserWindow 加载网页内容并发请求，仍可能触发跨域问题。

解决方案：

使用 nodeIntegration： 在主进程中发起请求而不是渲染进程。

```javascript
const { ipcMain } = require('electron');
const axios = require('axios');

ipcMain.handle('getData', async () => {
  const res = await axios.get('https://api.example.com/data');
  return res.data;
});
```

通过 session.webRequest 修改请求头：

```javascript
const { session } = require('electron');
session.defaultSession.webRequest.onBeforeSendHeaders((details, callback) => {
  details.requestHeaders['Origin'] = '*';
  callback({ requestHeaders: details.requestHeaders });
});
```


## WebSocket 通信

WebSocket 提供持久化、全双工的实时通信通道，非常适合用于聊天、数据推送、股票行情等应用。


### WebSocket 客户端实现

Electron 可以直接使用浏览器原生的 WebSocket API：


## 实例

参数说明：

- new WebSocket(url)：创建连接；
- socket.send(data)：发送消息；
- onmessage：监听服务器返回；
- onclose：监听连接关闭。


### 实时通信应用示例

假设我们构建一个实时聊天室界面：


## 实例

渲染进程的 HTML：


## 实例

这种模式可以轻松实现实时聊天、状态同步、协同编辑等功能。


## 原生网络模块

Electron 的主进程提供了 Node.js 的 net 模块，可以在更底层直接创建 TCP 或 IPC 连接，适用于定制化协议或本地服务交互。


### net 模块使用

net 模块允许你创建 TCP 客户端或服务器。

创建 TCP 服务器：


## 实例

TCP 客户端连接：


## 实例

参数说明：

- net.createServer(callback)：创建服务器；
- socket.write(data)：发送数据；
- socket.on('data')：接收数据；
- server.listen(port)：监听端口。


### session 管理

Electron 中的 session 模块可控制缓存、Cookie、代理等网络会话信息。


## 实例


### Cookie 处理


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Electron 网络与外部通信` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
