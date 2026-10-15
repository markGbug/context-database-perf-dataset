# JavaScript：JavaScript async/await

- 来源：[JavaScript async/await](https://www.runoob.com/js/js-async-await.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2795

## 本章内容

在讲解 async/await 之前，我们需要先理解 JavaScript 中的异步编程概念，可以参考：JavaScript 异步编程。

JavaScript 是单线程语言，意味着它一次只能执行一个任务。为了避免长时间运行的任务阻塞主线程，JavaScript 使用异步编程模型。


### 异步 vs 同步

- 同步（Synchronous）编程：代码按顺序执行，前一个操作完成后才会执行下一个
- 异步编程（Asynchronous）：某些操作被放入"任务队列"，主线程继续执行后续代码，等主线程空闲时再处理队列中的任务


## 实例


## 回调函数的问题

在 async/await 出现之前，JavaScript 主要使用回调函数处理异步操作，但这会导致"回调地狱"（Callback Hell）。


## 实例

这种嵌套结构使得代码难以阅读和维护。


## Promise 的引入

ES6 引入了 Promise 对象来解决回调地狱问题。


## 实例

虽然 Promise 改善了回调问题，但 then() 链式调用仍然不够直观。


## async/await 语法

ES2017 引入了 async/await，它建立在 Promise 之上，让异步代码看起来像同步代码一样。


### async 函数

在函数声明前添加 async 关键字，表示该函数是异步的：

async 函数总是返回一个 Promise：

- 如果返回值不是 Promise，会自动包装成 resolved Promise
- 如果抛出异常，会返回 rejected Promise


### await 表达式

await 只能在 async 函数内部使用：

await 会暂停 async 函数的执行，等待 Promise 完成：

- 如果 Promise 被 resolve，返回 resolve 的值
- 如果 Promise 被 reject，抛出错误（可以用 try/catch 捕获）


## 实际应用示例


### 基本用法


## 实例


### 错误处理


## 实例


### 并行执行

如果需要并行执行多个异步操作，可以使用 Promise.all：


## 实例


## 常见问题与最佳实践


### 1. 不要忘记 await


## 实例


### 2. 避免不必要的 async


## 实例


### 3. 顶层 await

在模块顶层可以直接使用 await（ES2022 特性）：


## 实例


### 4. 性能考虑

- 顺序执行 vs 并行执行：合理使用 Promise.all 提高性能
- 错误处理：确保所有可能的错误都被捕获


## 后续章节

- async/await 与传统 Promise 对比
- 总结

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript async/await` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
