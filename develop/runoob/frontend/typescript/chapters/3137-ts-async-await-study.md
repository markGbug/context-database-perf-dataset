# TypeScript：TypeScript async/await 异步编程

- 来源：[TypeScript async/await](https://www.runoob.com/typescript/ts-async-await.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3137

## 本章内容

async/await 是 ES2017 引入的异步编程语法糖，让异步代码看起来像同步代码。

上图展示了 async/await 相比传统 Promise 的优势：代码更简洁，执行流程更清晰。


## Promise 基础

Promise 代表一个异步操作的最终结果。


## 实例

运行结果：

```text
成功: 操作成功
```


## async 函数

使用 async 关键字声明异步函数。


## 实例

运行结果：

```text
结果: Hello, World!
数据: {"name":"Alice","age":25}
```


## await 关键字

await 等待 Promise 完成并获取结果。


## 实例

运行结果：

```text
开始...
结果: 完成!
结束
```


## 错误处理

使用 try/catch 处理异步错误。


## 实例

运行结果：

```text
捕获错误: 操作失败
```


## 并行执行

使用 Promise.all 并行执行多个异步操作。


## 实例

运行结果：

```text
串行完成: User1, User2
并行完成: User1, User2
```


## async/await 相比 Promise 的优势

- 代码更简洁、更易读
- 同步代码风格
- 更好的错误堆栈
- 易于调试


## 总结

- async：声明异步函数
- await：等待 Promise
- 错误处理：try/catch
- 并行：Promise.all


## 复习重点

- 能说明 `TypeScript async/await` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
