# Dart：Dart 并发与 Isolate

- 来源：[Dart 并发与 Isolate](https://www.runoob.com/dart/dart-isolates.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：学习笔记
- 章节序号：3655

## 本章内容

并发是指同时处理多个任务的能力。

Dart 的并发模型不同于传统的多线程，它使用 Isolate（隔离区）来实现并行计算。

本章介绍 Dart 的并发模型、Isolate 的概念与使用以及消息传递机制。


## Dart 并发模型

大多数编程语言使用共享内存的多线程模型，多个线程共享同一个内存空间。

这种模型的缺点是容易产生竞态条件（race condition）和死锁（deadlock）。

Dart 采用了不同的策略：每个 Isolate 拥有自己独立的内存堆，Isolate 之间不共享内存。

它们通过消息传递来通信，这从根本上避免了数据竞争问题。

Dart 的并发模型有三个层次：

大多数 Dart 程序的并发需求都可以通过 async/await 和 Future/Stream 来满足。Isolate 只在你需要进行大量 CPU 密集型计算时才有必要使用。过早引入 Isolate 会让代码变复杂，收益却不大。


## Isolate 概念与使用

Isolate 是 Dart 的并发单元，每个 Isolate 有自己独立的内存和事件循环。

主程序本身就在一个 Isolate（主 Isolate）中运行。


### 使用 Isolate.spawn 创建新 Isolate


## 实例

```text
主 Isolate 启动
主 Isolate 在等待结果的同时可以做其他事情...
新 Isolate 开始计算...
新 Isolate 计算完成，结果已发送
RUNOOB 计算结果: 1 到 10000000 的和 = 50000005000000
主 Isolate 结束
```


### 对比：有无 Isolate 的性能差异


## 实例

在 Flutter 应用中，如果在主 Isolate 中执行耗时的同步计算，会导致 UI 冻结。解决方案就是将计算任务放到单独的 Isolate 中，计算完成后通过消息将结果传回并更新 UI。


## 消息传递机制

Isolate 之间通过 SendPort 和 ReceivePort 进行消息传递。

消息必须是可序列化的（基本类型、String、List、Map 等），不能传递函数或闭包。


### 双向通信


## 实例

```text
主 Isolate: 启动
主 Isolate: 已建立与 Worker 的双向通信
Worker Isolate: 等待任务...
Worker Isolate: 收到数据 [1, 2, 3, 4, 5]
主 Isolate: 收到结果 [1, 4, 9, 16, 25]
Worker Isolate: 收到数据 [10, 20, 30]
主 Isolate: 收到结果 [100, 400, 900]
Worker Isolate: 收到退出信号，关闭
主 Isolate: Worker 已退出
RUNOOB 双向通信演示结束
```


### 使用 Isolate.run 简化（Dart 3.0+）

Dart 3.0 引入了 Isolate.run()，大大简化了单次计算任务的使用。


## 实例

```text
开始计算...
RUNOOB 计算结果: 333333283333335000000
计算完成
（如果在主 Isolate 中直接计算，会阻塞其他操作）
```

Isolate.run() 适合"执行一次计算并返回结果"的场景。如果你需要持续的、双向的通信（比如长时间运行的后台服务），则需要使用 Isolate.spawn() + SendPort/ReceivePort。


### Isolate 消息传递的限制


## 并发模型对比

Dart 的 Isolate 模型虽然避免了数据竞争，但代价是创建和通信的开销较大。不要创建成千上万个 Isolate——通常几个 Isolate 就足够了。对于 I/O 密集型任务，使用 async/await 是最佳选择。


## 复习重点

- 能说明 `Dart 并发与 Isolate` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
