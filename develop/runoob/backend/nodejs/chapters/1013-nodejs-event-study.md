# Node.js：Node.js EventEmitter

- 来源：[Node.js EventEmitter](https://www.runoob.com/nodejs/nodejs-event.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：学习笔记
- 章节序号：1013

## 本章内容

Node.js 所有的异步 I/O 操作在完成时都会发送一个事件到事件队列。

Node.js 里面的许多对象都会分发事件：一个 net.Server 对象会在每次有新连接时触发一个事件， 一个 fs.readStream 对象会在文件被打开的时候触发一个事件。 所有这些产生事件的对象都是 events.EventEmitter 的实例。

EventEmitter 是 Node.js 中用于创建、注册和触发事件的核心模块。

EventEmitter 是事件驱动编程的基础，可以帮助开发者轻松实现事件的发布与订阅机制。


## EventEmitter 类

events 模块只提供了一个对象： events.EventEmitter。

EventEmitter 的核心就是事件触发与事件监听器功能的封装。

你可以通过 require("events"); 来访问该模块。


## 实例

EventEmitter 对象如果在实例化时发生错误，会触发 error 事件。当添加新的监听器时，newListener 事件会触发，当监听器被移除时，removeListener 事件被触发。

下面我们用一个简单的例子说明 EventEmitter 的用法：


## 实例


## 复习重点

- 能说明 `Node.js EventEmitter` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
