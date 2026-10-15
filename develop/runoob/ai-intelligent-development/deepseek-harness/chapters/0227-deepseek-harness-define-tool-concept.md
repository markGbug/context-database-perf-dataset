# DeepSeek Harness：DeepSeek Harness 开发第一个工具：defineTool

- 来源：[DeepSeek Harness 第一个工具](https://www.runoob.com/deepseek-harness/deepseek-harness-define-tool.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：概念卡
- 章节序号：0227

## 本章内容

工具是 Agent 用来干活的函数，模型看到工具定义后决定调用。

本章节我们将用 defineTool 写出第一个工具 greet，并让模型真的调用它。


## 工具是什么

工具（tool）是一个描述清晰的函数，包含名称、说明、参数和输出格式。

模型在生成回复时，可以根据这些信息发起调用。

在 dsh 里，工具通过 ctx.tools.register 注册到工具注册表。


## defineTool 的完整结构

defineTool 是定义工具的 DSL，它接收一个对象，描述工具的全部信息。


## 创建 greet 工具

把 scratch-plugin/src/my-plugin.ts 替换为以下内容。


## 实例

inject 让 Cordis 等待工具注册表就绪。

defineTool 根据 parameters 推导并校验 args。

execute 返回 output.schema 声明的规范值。

output.render 再把规范值转换为面向模型的内容。


## 运行并调用

如果开发命令没在运行，重新启动：

```text
pnpm dsh web --patch ./scratch-plugin/cordis.yml
```

打开 http://127.0.0.1:3080，输入：

```text
Use the greet tool to greet RUNOOB.
```

模型可以调用 greet，并收到 Hello, RUNOOB! 这一工具结果。


## 关键点：schema 自动流入提示词

工具的 name、description、parameters、output 会自动组装进模型提示词。

模型"知道"有这样一个工具，就会在合适的时候调用。

你不需要手写函数签名给模型，schema 就是模型看到的接口。

规范值（canonical value）是 execute 返回、output.schema 声明的值。

它与"面向模型的内容"解耦：同一个规范值可以通过不同 render 变成不同格式。

提示：想查看更复杂的工具写法（嵌套 schema、后台工作、策略钩子），见官方工具编写参考。


## 小结与自测

defineTool 用 schema 描述工具，ctx.tools.register 注册它，模型看到 schema 后直接调用。

1. defineTool 的 execute 返回的是什么？

2. output.render 的作用是什么？

3. 模型是怎么知道要调用 greet 的？


## 记忆卡片

- 一句话定义：`DeepSeek Harness 第一个工具` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
