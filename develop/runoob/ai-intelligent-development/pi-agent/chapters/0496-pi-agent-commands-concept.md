# Pi Agent：Pi Agent 命令与快捷键注册

- 来源：[Pi Agent 命令与快捷键注册](https://www.runoob.com/pi-agent/pi-agent-commands.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：概念卡
- 章节序号：0496

## 本章内容

通过扩展注册自定义命令、键盘快捷键和 CLI 标志，让 Pi Agent 更好地适应你的工作流。


## 注册自定义命令

使用 pi.registerCommand() 注册用户可通过 / 调用的命令。

下面的扩展同时演示了基础命令和带参数自动补全的命令：


## 实例

保存后执行 /reload 加载扩展，在编辑区输入 /stats 即可看到效果：

```text
/stats
共 42 条消息
```

如果多个扩展注册了同名的命令，Pi Agent 会保留所有注册并按加载顺序添加数字后缀，例如 /review:1 和 /review:2。

这避免了扩展之间的命名冲突。


## 扩展主动发消息

除了被动响应命令和事件，扩展还可以主动驱动对话。

pi.sendMessage(message, deliverAs?) 用于注入自定义消息，pi.sendUserMessage(text, deliverAs?) 则模拟一条用户输入。

deliverAs 有三个取值：steer 是默认值，把消息插入当前轮；followUp 在本轮结束后追加；nextTurn 开启新一轮（仅 sendMessage 支持）。

sendUserMessage 总是会触发一轮回复，因为它对 AI 来说就是一次真实的用户发言。

流式输出期间调用这两个方法时，必须显式给出 deliverAs，否则会直接抛错。


## 实例

sendMessage 还支持 triggerTurn: true，在 agent 空闲时立即触发一次 LLM 响应。

两者的选择标准很简单：想让 AI 真正接话就用 sendUserMessage，只想提供参考信息就用 sendMessage。


## 命令上下文（ExtensionCommandContext）

命令的 handler 接收的是 ExtensionCommandContext，它继承自 ExtensionContext。

在普通上下文的基础上，它额外提供以下方法：

下面的命令把当前项目的所有会话列成选择列表，选中后直接切换过去：


## 实例

```text
/switch
┌ 选择要切换的会话：
│ > ~/.pi/agent/sessions/my-project/abc123.jsonl
│   ~/.pi/agent/sessions/my-project/def456.jsonl
└
已切换会话
```

会话替换的注意事项：withSession 回调中的 ctx 是一个全新的上下文。

不要使用旧的 pi 对象或命令回调中捕获的 ctx，它们在会话替换后会变成无效状态。


## 注册快捷键

使用 pi.registerShortcut() 注册自定义键盘快捷键。

下面把「切换 Plan 模式」绑到一个尚无内置占用的组合键上：


## 实例

启动后按下组合键即可触发：

```text
已切换 Plan 模式！
```

选择组合键前先核对默认快捷键表，避免覆盖内置绑定。

例如 ctrl+shift+p 已被「向后切换模型」占用，再注册同名组合键会导致两个行为互相抢键。

快捷键格式为 修饰键+按键，例如 ctrl+shift+g、alt+x 等。


## 注册 CLI 标志

使用 pi.registerFlag() 为 pi 命令添加自定义 CLI 参数。

下面的例子注册一个 --plan 布尔标志，用于让 AI 先出计划再动手：


## 实例

使用方式：

```text
$ pi --plan "帮我实现用户认证功能"
```


## 扩展间通信

使用 pi.events 在扩展之间共享事件。

发送方不需要知道谁在监听，监听方也不需要知道事件从哪里来：


## 实例


## 获取已注册的命令

使用 pi.getCommands() 获取当前会话中所有可用的命令。

下面的例子注册一个 /my-commands 命令，用来列出所有由扩展注册的命令：


## 实例

```text
/my-commands
扩展命令 2 个：/stats、/deploy
```

每个命令条目包含以下字段：


## 动态工具管理

运行时管理工具的启用和禁用。

典型用途是临时关掉写操作工具，让 AI 在一次任务里只能读不能改：


## 实例

这里的 setActiveTools 与命令行的 --tools / --exclude-tools 参数作用于同一个工具集合。

CLI 参数决定启动时的初始集合，setActiveTools 在运行时动态调整，两者可以配合使用。

传入 setActiveTools 的变更必须是增量的（additive），在同一次调用中移除当前已激活的工具会失去延迟加载优化。

另外，激活带 promptSnippet 或 promptGuidelines 的工具会重建系统提示词，即使模型支持延迟加载，也可能使缓存的提示词前缀失效。


## 记忆卡片

- 一句话定义：`Pi Agent 命令与快捷键注册` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
