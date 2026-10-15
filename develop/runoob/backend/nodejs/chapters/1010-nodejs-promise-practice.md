# Node.js：Node.js Promise

- 来源：[Node.js Promise](https://www.runoob.com/nodejs/nodejs-promise.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：练习笔记
- 章节序号：1010

## 本章内容

Promise 是 Node.js 中处理异步操作的核心概念之一。

Promise 提供了一种更优雅的方式来管理异步代码，避免了传统的回调地狱（Callback Hell）问题。

本文将详细介绍 Promise 的概念、用法和常见模式。


## 什么是 Promise？

Promise 是一个表示异步操作最终完成或失败的对象。它有三种状态：

- Pending（等待中）：初始状态，既不是成功，也不是失败
- Fulfilled（已成功）：操作成功完成
- Rejected（已失败）：操作失败

Promise 的状态一旦改变（从 pending 变为 fulfilled 或 rejected），就不会再改变。


## 创建 Promise

在 Node.js 中，可以使用 Promise 构造函数创建新的 Promise 对象：


## 实例


## 使用 Promise

Promise 提供了 .then() 和 .catch() 方法来处理成功和失败的情况：


## 实例


## Promise 链式调用

Promise 的强大之处在于可以链式调用多个异步操作：


## 实例


## Promise 的静态方法

Promise 提供了一些有用的静态方法：


### Promise.all()

等待所有 Promise 完成，或任意一个 Promise 失败：


## 实例


### Promise.race()

返回最先完成或失败的 Promise：


## 实例


## 错误处理

Promise 的错误处理可以通过 .catch() 或 .then() 的第二个参数实现：


## 实例


## async/await 语法

ES2017 引入了 async/await 语法，让 Promise 的使用更加直观：


## 实例


## 最佳实践

- 总是处理错误：不要忽略 .catch() 或 try-catch
- 避免嵌套：使用链式调用或 async/await 保持代码扁平
- 命名 Promise：给 Promise 变量起有意义的名称
- 返回 Promise：在函数中返回 Promise 以便链式调用


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Node.js Promise` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
