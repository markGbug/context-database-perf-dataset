# Swift：Swift 版本新特性

- 来源：[Swift 版本新特性](https://www.runoob.com/swift/swift-new-features.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：学习笔记
- 章节序号：3452

## 本章内容

Swift 从 2014 年发布到现在，语言面貌已经换过好几轮。

老教程里常见的 ++、C 风格 for、println 之所以编译不过，就是版本差异造成的。

本文按版本梳理关键特性，重点讲 Swift 6 的严格并发和迁移路径，最后简单介绍 Swift 5.9 引入的宏。


## 版本时间线

先看一张总表，把「哪个版本带来了什么」对齐到时间轴上。

表中所有特性都能在 Swift Evolution 提案页查到，提案页会标注 Implemented in Swift X。

注意：表中没有写具体版本号的小项，是因为官方提案页没有明确标注 Implemented in Swift X。写文档时不确定的版本号宁可不写，也不要编。


## 几个高频特性速览

下面挑出日常最常用、也最容易和旧教程冲突的几组特性，各配一段可运行的代码。


### some 与 any

some 表示「某个具体的遵循类型，但我不告诉你它是谁」，编译期就确定了真实类型。

any 表示「任何遵循该协议的类型」，运行时才知道，代价是动态派发。


## 实例

```text
你好，Runoob
你好，www.runoob.com
你好，RUNOOB
```

更完整的取舍见《Swift some 与 any》。


### if let 简写与 if 表达式

if let 同名简写省掉了重复的变量名，从 Swift 5.7 起可用（SE-0345）。

if / switch 可以直接作为表达式给变量赋值，从 Swift 5.9 起可用（SE-0380）。


## 实例

```text
站点：www.runoob.com
及格
3
```


### async / await 与 actor

Swift 5.5 引入的并发模型包含三块：async / await 负责挂起与恢复，actor 负责隔离可变状态，Task 与任务组负责结构化并发。


## 实例

```text
["文章 1", "文章 2"]
字符总数：12
计数：100
```

并发章节的完整内容见《Swift async 与 await》和《Swift actor 与数据隔离》。


## Swift 6 严格并发与迁移建议

Swift 6 最大的变化不是新语法，而是把并发安全检查从「提醒」变成了「强制」。

数据竞争指的是两个线程同时访问同一块内存，其中至少一个是写操作，且没有同步措施。

这类 bug 往往在测试环境不复现，上线后才偶发崩溃，所以编译器宁愿在编译期拦住你。


### Swift 6 语言模式做了什么

Swift 6 编译器同时支持 Swift 5 和 Swift 6 两种语言模式，通过 -swift-version 5 或 -swift-version 6 切换。

在 Swift 6 模式下，原本只是警告的并发问题会变成编译错误，构建直接失败。


### Sendable 与 actor 的配合

Sendable 是一个标记协议，表示「这个类型的值可以安全地跨隔离域传递」。

值类型且所有存储属性都是 Sendable 时，编译器会自动推导出遵循关系，不需要手写。


## 实例

把上面的代码用 Swift 6 语言模式运行，输出如下。

```text
$ swift -swift-version 6 RunoobConfig.swift
["www.runoob.com:30"]
```


### 典型报错长什么样

下面这段代码在 Swift 5 模式下能跑，但在 Swift 6 模式下编译失败，因为全局可变状态没有隔离。


## 实例

编译器给出的第一条诊断是：

```javascript
error: var 'sharedBox' is not concurrency-safe because it is nonisolated global shared mutable state [#MutableGlobalVariable]
```

注意：上面这段代码故意不完整，就是为了展示真实的编译错误，不要直接拿去运行。这类全局可变状态正确的做法是收进 actor，或者改成 let 常量。


### 三种常见的修复手段

绝大多数报错可以归到三条路径：加隔离、加 Sendable、或者显式声明「由我负责」。

最推荐的是加隔离，把 UI 状态标成 @MainActor，编译器会自动保证它只在主线程被访问。


## 实例

```text
Swift 教程
```

对于确实无法消除的旧代码，可以用 nonisolated(unsafe) 明确关掉某个变量的检查。

这个关键字等于对编译器说「我知道它不安全，责任在我」，所以必须配注释说明理由。


## 实例

```text
2
```


### 从 Swift 5 迁移到 Swift 6 的步骤

不要指望一次性把所有警告清零，官方推荐的做法是分阶段推进。

关键是先让问题可见，再逐个模块收口。

注意：Swift 6 语言模式不是强制的，Swift 5 模式仍受支持。但新项目建议直接开 Swift 6，越晚迁移成本越高。

更详细的数据竞争分析与 Sendable 规则见《Swift Sendable 与 Swift 6 严格并发》。


## 宏（Swift 5.9）简介

宏的作用是在编译期把一小段代码展开成另一段代码，运行时不产生额外开销。

它和 C 的宏有本质区别：Swift 宏是类型安全的，而且实现本身是一段普通 Swift 程序，在编译期由编译器调用。

Swift 5.9 引入的宏分两大类，见下表。

最常用的现成宏是 Observation 框架提供的 @Observable，它替你把属性观察代码全部生成出来。


## 实例

```text
Swift 教程 阅读量：1
```

如果你要自己写宏，需要建一个 SwiftPM 包：声明放对外模块，实现在另一个编译期模块里。

下面这段是声明部分的写法，属于纯语法片段，需要完整的宏包才能编译，不能单独用 swift 命令运行。


## 实例

注意：宏的实现代码在编译期执行，可以读取源码结构，但不能访问运行时的数据。写自定义宏之前，先确认标准库或系统框架里有没有现成的，绝大多数场景都不需要自己实现。


## 常见问题

下面几个问题是版本升级过程中最常被问到的。


### 升级 Swift 版本需要重写代码吗？

大多数版本是向后兼容的，语法层面的破坏性改动主要集中在 Swift 2 到 3 那一轮。

Swift 6 的主要迁移成本在并发检查，而不是语法。


### 怎么确认某个特性从哪个版本开始可用？

查对应的 Swift Evolution 提案页，页面顶部会写 Implemented in Swift X。

也可以用 #available 判断运行时系统版本，但语言特性本身由编译器版本决定，不能靠运行时判断。


## 后续章节

- Swift 6 语言模式一定要打开吗？
- @Observable 和以前的 ObservableObject 有什么区别？
- 宏会让编译变慢吗？

## 复习重点

- 能说明 `Swift 版本新特性` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
