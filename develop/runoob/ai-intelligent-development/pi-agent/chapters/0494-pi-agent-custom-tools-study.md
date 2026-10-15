# Pi Agent：Pi Agent 自定义工具开发

- 来源：[Pi Agent 自定义工具开发](https://www.runoob.com/pi-agent/pi-agent-custom-tools.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：学习笔记
- 章节序号：0494

## 本章内容

通过 Extension 注册自定义工具，让 AI 能够调用你编写的函数来完成特定任务。


## 工具注册基础

使用 pi.registerTool() 注册一个 AI 可调用的工具：


## 实例

注册完成后，AI 会根据 description 和 promptSnippet 自主决定何时调用 todo 工具。

例如用户说"帮我把写周报加进待办"，AI 会发起下面这次调用：

```text
tool_call: todo
{
  "action": "add",
  "text": "写周报"
}
```

execute 执行后，返回给 AI 的文本如下：

```text
待办已新增：写周报（共 1 项）
```

AI 拿到这个结果后，会用自然语言向用户确认，例如"已把「写周报」加入待办列表，目前共 1 项"。

除了从 toolResult 的 details 重建状态，跨重启持久化还有另一条路：pi.appendEntry()。

它把自定义条目直接写进会话文件，配合 pi.registerEntryRenderer() 还能在对话记录里渲染出来。

自定义条目不会进入 LLM 上下文，因此不占用 token。

但它们会随会话一起保存，并且在 /tree 分支中保留。


## 工具定义详解

registerTool 的配置对象包含以下字段，其中 name、parameters 和 execute 是核心。

promptGuidelines 中的每条指南都必须明确指出工具名称。

不要写「使用此工具时…」，而要写「使用 my_tool 时…」，因为 AI 无法根据「此」来判断指的是哪个工具。


## execute 函数详解

execute 函数接收以下参数：

返回值格式：


## 实例

要标记工具执行失败，使用 throw new Error()，不要尝试在返回值中设置错误标记。

只有抛出异常才能将 isError 设为 true，并通知 LLM 发生了错误。


## StringEnum 与类型安全

使用 StringEnum 而不是 Type.Union/Type.Literal 来定义枚举参数：


## 实例


## 文件修改安全队列

如果你的工具会修改文件，使用 withFileMutationQueue() 参与文件修改队列：


## 实例

文件修改队列确保同一文件的并发修改不会互相覆盖——当内置 edit 工具和你的自定义工具同时修改同一个文件时，它们会排队执行。


## 输出截断

工具输出必须截断，避免撑满 LLM 上下文窗口。内置限制为 50KB（约 1 万 token）和 2000 行：


## 实例

对一个超过限制的大日志文件，工具的返回文本末尾会带上截断说明：

```text
[2026-08-31 10:02:11] server started on port 3000
[2026-08-31 10:02:12] GET / 200 12ms
[2026-08-31 10:02:12] GET /static/app.js 200 4ms
...

[输出已截断：2000/8642 行（49.9KB/210.3KB）]
```

截断不是可选的。

过大的工具输出会导致上下文溢出、压缩失败和模型性能下降，始终对工具输出进行截断处理。


## 覆盖内置工具

你可以通过注册同名工具来覆盖内置工具（read、bash、powershell、edit、write、grep、find、ls）。

```text
$ pi -e ./tool-override.ts
```

下面用 registerTool 覆盖内置的 read 工具，为每次文件读取加一条日志：


## 实例

加载这个扩展后，AI 每次读文件都会在终端打印一行 [read] 日志。

覆盖时，渲染器（renderCall/renderResult）会按槽位继承——如果你省略了 renderCall，内置的 renderCall 仍会使用。

这让你可以在不重写 UI 的情况下为内置工具添加日志或权限控制。

但对于 promptSnippet 和 promptGuidelines，它们不会从内置工具继承，需要显式定义。

还有一个更隐蔽的约束：你的实现必须与内置工具的结果形状完全一致，包括 details 字段。

以 read 为例，入参需要支持 offset 和 limit 两个可选参数，这样 AI 按分页方式读取大文件时才能拿到预期内容。

返回值中的 details 也必须与内置 read 的 ReadToolDetails 形状一致，否则 UI 渲染会缺信息，会话的状态跟踪也会受影响。

上面这个日志扩展示例只做演示，正式覆盖内置 read 时请按内置实现补全参数与 details。


## 复习重点

- 能说明 `Pi Agent 自定义工具开发` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
