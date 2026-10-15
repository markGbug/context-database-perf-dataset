# Node.js：Node.js async/await

- 来源：[Node.js async/await](https://www.runoob.com/nodejs/nodejs-async-await.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：练习笔记
- 章节序号：1011

## 本章内容

在 Node.js 中，async/await 是一种处理异步操作的语法糖。

async/await 基于 Promise，但让异步代码看起来更像同步代码，极大地提高了代码的可读性和可维护性。

async 关键字用于声明一个函数是异步的，而 await 关键字用于等待一个 Promise 的解决（resolve）或拒绝（reject）。

使用 async/await 可以避免回调地狱（callback hell）并使错误处理更加直观。

JavaScript 是单线程的，遇到异步任务（如 setTimeout 或网络请求）时，会交给 浏览器 API 处理，完成后将回调放入消息队列。

事件循环不断检查调用栈是否为空，如果是，就从队列中取出回调推入调用栈执行。这样既不会阻塞主线程，又能按顺序处理异步结果。


## 基本语法


### async 函数

任何函数都可以通过添加 async 关键字变成异步函数：

async 函数总是返回一个 Promise。如果返回值不是 Promise，它会被自动包装成 Promise。


### await 表达式

await 只能在 async 函数内部使用，它会暂停函数的执行，等待 Promise 解决，然后继续执行并返回结果：


## 错误处理


### try/catch 方式

处理 async/await 错误最常用的方法是使用 try/catch：


## 实例


### 直接处理 Promise

你也可以直接处理返回的 Promise：


## 实例


## 实际应用示例


### 并行执行多个异步操作

使用 Promise.all 结合 async/await 可以并行执行多个异步操作：


## 实例


### 数据库操作示例


## 实例


## 最佳实践

- 总是处理错误：不要忽略 await 可能抛出的错误，使用 try/catch 或 .catch() 处理
- 避免不必要的 await：如果不需要等待结果，可以直接返回 Promise
- 合理使用并行：多个独立的异步操作应该并行执行（使用 Promise.all）
- 保持代码清晰：避免过深的 async/await 嵌套，必要时提取函数
- 注意性能影响：每个 await 都会暂停函数执行，在循环中要特别注意


## 常见问题


### async/await 与 Promise 的关系

async/await 是建立在 Promise 之上的语法糖。任何 async 函数都返回 Promise，任何 await 后面都可以接 Promise。


### 为什么我的 async 函数返回 undefined？

这可能是因为忘记在 await 前使用 return，或者在 Promise 解决前函数就退出了。


### 可以在顶层使用 await 吗？

在 ES 模块中（文件以 .mjs 结尾或 package.json 中 "type": "module"），可以直接在顶层使用 await。在 CommonJS 模块中，需要包裹在 async 函数中。


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Node.js async/await` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
