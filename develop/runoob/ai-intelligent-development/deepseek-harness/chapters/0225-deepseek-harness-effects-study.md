# DeepSeek Harness：DeepSeek Harness 自动清理与 ctx.effect()

- 来源：[DeepSeek Harness 自动清理](https://www.runoob.com/deepseek-harness/deepseek-harness-effects.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：学习笔记
- 章节序号：0225

## 本章内容

上一章节 DeepSeek Harness 加载本地插件 打印一行日志就结束了，但真实插件会注册监听、工具、定时器。

本章节解决一个问题：插件卸载时，这些资源谁来清理？

注册交给 ctx，清理也交给 ctx。


## 自动清理机制

通过 ctx 注册的任何东西——事件监听、工具、定时器——在插件卸载时都会被自动清理。

你不需要手动 removeListener 或 clearInterval。

框架能自动清理，是因为所有通过 ctx 的注册都被记在插件的 Fiber 作用域里。

卸载时，框架按注册顺序的逆序撤销它们。


## 哪些操作会被自动追踪

下面这些操作都会被自动追踪和清理。


## ctx.effect()：手动资源交给框架

有些资源不在上面的列表里，比如一个网络连接。

用 ctx.effect() 告诉框架怎么清理它。

ctx.effect 接收一个回调，回调里创建资源并返回一个清理函数（disposer）。

这个 disposer 会在插件卸载时执行。

disposer（清理函数）是 ctx.effect 回调的返回值。

它描述了"如何销毁这次创建的资源"。

插件卸载时，框架会调用它。

下面是一个心跳定时器的例子：


## 实例

如果卸载时什么都不用做，disposer 可以不写。

但一旦创建了定时器、连接这类资源，就一定要返回对应的清理函数。


## 执行顺序的细节

插件卸载时，处置器按注册顺序的逆序开始调用。

多个异步处置器会并发执行，不保证逐个完成。

存在顺序依赖的清理步骤，必须放进同一个 ctx.effect() 返回的处置器中，由该处置器负责串行等待。

提示：这条规则意味着先注册后清理——后注册的资源先被清理。


## 小结与自测

通过 ctx 注册的资源在卸载时自动清理；手动资源用 ctx.effect() 提供 disposer。

- 1. 通过 ctx 注册的定时器需要手动 clearInterval 吗？
- 2. ctx.effect(() => disposer) 的 disposer 何时执行？
- 3. 为什么有顺序依赖的清理要放进同一个 effect？


## 复习重点

- 能说明 `DeepSeek Harness 自动清理` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
