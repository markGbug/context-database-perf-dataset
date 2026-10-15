# DeepSeek Harness：DeepSeek Harness 事件系统：emit / bail / serial / waterfall

- 来源：[DeepSeek Harness 事件系统](https://www.runoob.com/deepseek-harness/deepseek-harness-events.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：学习笔记
- 章节序号：0233

## 本章内容

插件之间怎么松耦合通信？事件就是 Cordis 的通信核心机制。

Harness 大量使用事件来实现可扩展的扩展点，这一篇把五种分发模式讲清楚。


## 基本用法

事件分监听与触发两端。


## 实例

通过 ctx.on 注册的监听器，会在插件卸载时自动移除。


## 五种分发模式

Cordis 提供多种分发模式，适用于不同的交互契约。

每个事件有且只有一种分发模式，且只能通过对应方法分发。

官方入门文档把 waterfall 标为「不 await」；但由于监听器通常是异步函数，教程示例里普遍写 await ctx.waterfall(...) 来等待整条处理链的最终结果。记住这个差别即可，两种写法都不算错。


## emit：广播

所有监听器同步执行，返回值会被忽略。


## 实例


## bail：短路

监听器按顺序运行，第一个不是 null、false 或 undefined 的返回值会成为最终结果。


## 实例


## serial：顺序执行

监听器按注册顺序依次执行，并等待异步结果。

第一个不是 null、false 或 undefined 的返回值会终止后续执行。


## 实例


## waterfall：流水线

每个监听器可以包装下游返回值，形成处理链。

监听器接收 (...args, next)，调用 next() 会执行下游监听器，下游返回值通过 next() 返回给当前包装层。


## 实例

waterfall 监听器必须调用 next()。不调用 next 会短路整个流水线，这是故意为之的设计，用于实现拦截或网关逻辑。

策略监听器在拥有决策权时，可以不调用 next() 直接返回，从而拦住整条链。

仅做标注或观察的监听器则必须委托给下游。


## 类型安全的事件

用 TypeScript 声明合并为事件提供类型安全。


## 实例


## Cordis 事件与会话记录

Harness 的 Cordis 事件遵循 namespace/action 命名，例如 agent/step、agent/request、agent/request-error、tools/result 和 session/event。

注意区分两类事件：

turn/*、step/*、tool/call、tool/result 和 compaction/* 是持久化的会话事件类型，不是同名 Cordis 事件。

需要观察它们时，监听 session/event 并检查 event.type。


## 动手示例：日志插件

官方文档用下面这个插件记录工具调用与工具结果，监听的是 Cordis 事件 tools/result。


## 实例

这个插件在 Agent 每次调用工具后，把工具名、参数和结果摘要打到终端。

监听器通过 ctx.on 注册，插件卸载时会被自动移除。


## 小结自测

五种分发模式覆盖「广播、决策、按序、流水线、并行」五类契约；waterfall 必须调用 next()；declare module 合并让事件名与参数有类型保障。

自测一下：

- 五种分发模式分别用哪个方法触发？哪些有返回值？
- waterfall 监听器不调用 next() 会怎样？这是 bug 还是设计？
- turn/start 这类持久化会话事件，应该监听哪个事件、检查哪个字段？


## 复习重点

- 能说明 `DeepSeek Harness 事件系统` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
