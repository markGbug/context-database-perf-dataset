# TypeScript：TypeScript Promise 详解

- 来源：[TypeScript Promise](https://www.runoob.com/typescript/ts-promise.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3138

## 本章内容

Promise 是 JavaScript 异步编程的基础，TypeScript 对 Promise 有完整的类型支持。

通过泛型参数，可以精确地指定 Promise 解决值和拒绝值的类型。


## 为什么需要 Promise

在 JavaScript 中，很多操作是异步的，如网络请求、文件读取、定时器等。

Promise 提供了统一的异步编程接口，让异步代码更容易编写和管理。

TypeScript 通过泛型支持，让 Promise 的类型安全得到了保障。

概念说明：Promise 是一个对象，表示一个异步操作的最终结果。它有三种状态：pending（进行中）、fulfilled（已成功）、rejected（已失败）。


## 创建 Promise

使用 Promise 构造函数创建 Promise，传入执行器函数。


## 实例

运行结果：

```text
完成: 成功!
```

泛型说明：Promise<T> 中的 T 是 Promise 成功解决时的值的类型。这让 TypeScript 能够推断返回值的类型。


## Promise 链式调用

then 和 catch 方法返回新的 Promise，可以链式调用。


## 实例

运行结果：

```text
最终结果: 12
Promise 链: [object Promise]
```

链式调用：每个 then 会返回一个新的 Promise，这允许我们按顺序执行多个异步操作。


## Promise.all

Promise.all 等待所有 Promise 完成，返回一个包含所有结果的数组。


## 实例

运行结果：

```text
全部完成: 1,2,3
总和: 6
```

注意：如果任何一个 Promise 失败，Promise.all 会立即 rejection，不会等待其他 Promise 完成。


## Promise.race

Promise.race 返回最先完成（无论成功或失败）的 Promise 的结果。


## 实例

运行结果：

```text
最先完成: p3
```

应用场景：Promise.race 常用于实现超时功能：把一个长时间操作的 Promise 和一个超时 Promise 竞争。


## Promise.allSettled

Promise.allSettled 等待所有 Promise 结束（无论成功或失败），返回每个 Promise 的状态和结果。


## 实例

运行结果：

```text
Promise 0: 成功
Promise 1: 失败
Promise 2: 完成
```

区别：Promise.all 会在第一个失败时立即停止；Promise.allSettled 会等待所有 Promise 结束。


## Promise 类型注解

TypeScript 的泛型支持让 Promise 的类型声明变得精确。


## 实例

类型推断：TypeScript 会根据泛型参数自动推断 Promise 的返回类型，这让我们在 async/await 中也能获得完整的类型提示。


## 注意事项

- 泛型参数：始终为 Promise 指定泛型参数，明确返回类型
- 错误处理：记得使用 catch 处理 Promise 失败的情况
- all vs allSettled：需要全部结果时用 allSettled，需要快速失败时用 all
- async/await：现代代码推荐使用 async/await，语法更简洁

最佳实践：优先使用 async/await 语法，它本质上还是基于 Promise，但写起来像同步代码。


## 总结

Promise 是 TypeScript 异步编程的核心。

- Promise：异步操作容器，有 pending/fulfilled/rejected 三种状态
- then/catch：链式处理异步结果
- Promise.all：等待全部完成，任一失败则整体失败
- Promise.race：返回最先完成的结果
- Promise.allSettled：等待全部结束，返回每个的状态

建议：使用 async/await 语法配合 Promise，让异步代码既类型安全又易于阅读。


## 复习重点

- 能说明 `TypeScript Promise` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
