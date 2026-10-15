# Pi Agent：Pi Agent 核心概念

- 来源：[Pi Agent 核心概念](https://www.runoob.com/pi-agent/pi-agent-concepts.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：练习笔记
- 章节序号：0478

## 本章内容

在正式使用 Pi Agent 之前，先了解它的核心概念和工作方式，能帮助你更快上手。


## 一句话理解 Pi Agent

Pi Agent 是一个运行在终端里的 AI 编程助手。

启动后你会看到类似聊天软件的界面，输入自然语言需求，AI 就能读取你的代码、执行命令、修改文件。


## 四种运行模式

Pi Agent 支持四种运行模式，适应不同场景：

交互模式直接启动，进入 TUI 界面：

```text
$ pi
Pi Agent 0.1.x  |  ~/projects/runoob-demo
claude-sonnet-4  |  上下文 2%  |  $0.0000
>
```

Print 模式回答完就退出，适合放进脚本：

```text
$ pi -p "总结这个项目"
这是一个 TypeScript 命令行工具，核心逻辑位于 src/ 目录，包含会话管理、工具调度和扩展加载三个模块。
Tokens: 1.2k 输入 / 320 输出  |  费用 $0.0081
```

JSON 模式把每个事件输出为一行 JSON，方便程序解析：

```text
$ pi --mode json -p "总结这个项目"
{"type":"session","id":"a1b2c3d4"}
{"type":"message_start","role":"assistant"}
{"type":"message_end","usage":{"input":1200,"output":320}}
```

RPC 模式通过 stdin/stdout 收发 JSONL 消息，供编辑器插件调用：

```text
$ pi --mode rpc
{"id":1,"method":"prompt","params":{"message":"列出 src 目录"}}
{"id":1,"result":{"state":"idle","messages":2}}
```

作为初学者，你大部分时间都在交互模式下工作。

当你熟练后，Print 模式可以用于脚本自动化。


## 内置工具

Pi Agent 启动后会默认给予 AI 下面四种内置工具，另有 grep、find、ls 三个只读工具可选开启：

三个只读工具通过 --tools 参数手动开启，例如 pi --tools read,grep,find,ls。


## 扩展体系

Pi Agent 通过以下五种方式扩展功能：

作为初学者，你不需要立即理解所有扩展方式。

先从基础使用开始，随着需求增长再逐步探索扩展系统。


## 文件加载顺序

Pi Agent 启动时会自动加载项目指令文件，让你可以约定 AI 的行为规范：

项目级的配置会从父目录向上遍历加载，最终和当前目录的配置合并。

如果你之前使用 Claude Code，可以直接复用已有的 CLAUDE.md 文件，Pi Agent 会自动识别加载。


## 会话与分支

Pi Agent 的会话系统是其最独特的特性之一。

每次对话会自动保存为一个会话文件，存放在 ~/.pi/agent/sessions/ 中。

会话内部是树状结构：你可以在任意历史节点「分叉」出新的探索方向，而不会丢失之前的对话。

这在你需要试验不同的实现方案时非常有用——每条思路都可以独立保留、随时回溯。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pi Agent 核心概念` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
