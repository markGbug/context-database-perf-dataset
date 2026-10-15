# AI Agent（智能体）：Loop Engineering（循环工程）

- 来源：[Loop Engineering](https://www.runoob.com/ai-agent/loop-engineering.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：概念卡
- 章节序号：0029

## 本章内容

Loop Engineering（循环工程）是 2026 年 6 月在 AI 编程社区迅速传播的一个新概念，由 Google 工程师 Addy Osmani 系统整理，Anthropic Claude Code 负责人 Boris Cherny 和开发者 Peter Steinberger 分别在公开场合提出了相同的观点。

本文将带你从零理解什么是 Loop Engineering、它与 Prompt Engineering 的本质区别、构成一个完整 Agent Loop 的六大要素，以及如何设计自己的第一个可运行的 Loop。


### AI 工程的演进过程

过去两年，AI 开发的重点正在不断变化：从研究如何写好提示词（Prompt），逐步发展到组织上下文（Context）、编排工具与流程（Harness），再到构建能够自主运行、持续交付结果的循环系统（Loop）。

```text
Prompt：怎么问 AI
↓
Context：给 AI 什么信息
↓
Harness：如何组织 AI 的能力
↓
Loop：如何让 AI 持续创造结果
```


## Loop Engineering 的起源

Loop Engineering 的出现有一个清晰的时间节点：2026 年 6 月。


### 引爆点：两句话，百万次转发

2026 年 6 月初，Anthropic Claude Code 负责人 Boris Cherny 在一次公开演讲中说道：

"I don't prompt Claude anymore. I have loops running. They're the ones prompting Claude and figuring out what to do. My job is to write loops." （我不再直接提示 Claude 了。我有一套 Loop 在运行，它们负责提示 Claude 并决定下一步做什么。我的工作是编写 Loop。）

几天后，2026 年 6 月 7 日，开发者 Peter Steinberger——开源 AI Agent 项目 OpenClaw（GitHub 历史上获星最快的新仓库）的创作者——发了一条十二个字的推文：

"You shouldn't be prompting coding agents anymore. You should be designing loops that prompt your agents." （你不应该再手动提示 AI 编程助手了。你应该设计让 Agent 自己提示自己的 Loop。）

- Prompt Engineering 是「教 AI 怎么做」
- Loop Engineering 是「设计一个系统，让 AI 自己持续做」

这两句话在 AI 开发者社区引发了巨大的讨论，因为它们精准地描述了一种很多人已经感受到但尚未命名的趋势：提示词写得好不好，已经不是瓶颈了；瓶颈在于你为 Agent 设计的整套运行系统。

随后，Addy Osmani 在 Substack 发表了长文，将这一实践正式命名并系统化为 Loop Engineering，使其成为独立的工程学科。


### 背景：AI 编程工具的三代演进

Loop Engineering 并非凭空而来，它是 AI 编程工具能力演进的自然结果。

第三代工具的出现意味着，工程师的核心竞争力从会写提示词变成了会设计 Loop。


## 什么是 Loop Engineering

Loop Engineering 是设计、运营和持续改进反馈循环的工程实践，这些循环使 AI 编程 Agent 能够自主完成规划、执行代码修改、观察结果并在多轮迭代中完成任务。

用一句话概括：

Loop Engineering 是把你从"提示 Agent 的人"变成"设计提示 Agent 的系统"的工程师。


### 什么是 Loop（循环）

一个 Loop 是一个递归目标系统：你定义一个目的，Agent 不断迭代，直到工作真正完成。

每个 Agent 在执行任务时已经内置了一个"内循环"：感知（Perceive）→ 推理（Reason）→ 行动（Act）→ 观察（Observe），然后再次循环。

Loop Engineering 工作在这个内循环的上一层：

你不再坐在 Agent 旁边，为每一步打下一条指令。你在设计一套外部系统，它替你驾驶内循环，而你去做更有判断价值的事。


### Loop Engineering 与 Prompt Engineering 的区别

Prompt Engineering 并没有消亡。一个 Loop 是由多个 Prompt 组成的，写得差的 Prompt 放进 Loop 里只会让糟糕的工作以更快的速度产出。Loop Engineering 是在 Prompt Engineering 之上的层次，而不是替代它。

三个层次的完整技术栈：


## Loop 的核心循环

一个 Agent Loop 的基础结构由五个阶段构成，它们首尾相连，不断迭代。

Loop 的力量不在于任何单独的步骤，而在于闭环。测试失败不只是一条错误消息，它是新的上下文；类型错误不只是阻断，它是一个关于错误假设的信号；Code Review 评论不只是反馈，它是驱动下一步行动的新观察。


## 六大构成要素

一个能够真正独立运行的 Loop 需要五个核心组件，加上一个贯穿始终的记忆系统，缺一不可。


### 要素一：自动触发器（Automations）

自动触发器是 Loop 的心跳。没有自动触发，Loop 就只是"你做了一次的操作"，而不是真正意义上的循环。

触发器定义了：什么时候？做什么？

在 Claude Code 中，使用 /loop 命令创建定时触发的 Loop：


## 实例

在 OpenAI Codex 中，Automations 有专属的 UI 面板，你可以设置项目、Prompt、节奏（cadence），以及是在本地检出还是后台 Worktree 中运行。发现内容的运行会进入 Triage 收件箱，未发现内容的会自动归档。

Token 成本警告：带验证子 Agent 的定时 Loop 每次触发都会消耗 Token，且消耗量因任务复杂度变化显著。建议先设置较慢的节奏（如每天一次），观察几天成本后再加快频率。


### 要素二：并行隔离（Worktrees）

当你同时运行多个 Agent 时，文件冲突是最容易出问题的地方。两个 Agent 同时写同一个文件，就像两个工程师同时提交到同一行代码，结果是灾难性的。

Git Worktree 是解决方案：为每个 Agent 提供独立的工作目录，各自在独立的分支上操作，共享同一个 Git 历史，但文件改动完全隔离。


## 实例

Worktree 消除了机械性的文件冲突，但不能消除审查瓶颈。你处理和批准代码变更的速度，才是决定你能并行运行多少个 Agent 的真正上限，而不是工具能开多少个 Worktree。


### 要素三：技能文件（Skills）

Skills（技能文件）解决的是一个每次都在浪费的成本：每次新对话，Agent 都要从零推断你的项目规范。

Skill 是一个包含 SKILL.md 文件的文件夹，写明了项目约定、构建步骤、"我们不这样做是因为那次事故"等知识。Agent 在每次会话开始时加载 Skill，而不是每次都重新猜测。


## 实例


### 要素四：连接器（Connectors / MCP）

一个只能看到本地文件系统的 Loop 能做的事情非常有限。连接器（基于 MCP——模型上下文协议）让 Agent 能够读取 Issue 追踪、查询数据库、调用 API、在 Slack 发消息。

这是"Agent 说'这里是修复方案'"和"Loop 自动开 PR、关联 Ticket、CI 通过后通知频道"之间的核心差异。

Claude Code 和 OpenAI Codex 均原生支持 MCP 协议，为一个工具编写的连接器通常可以在两者中通用。


## 实例：在 Claude Code 中配置 MCP 连接器

给 Agent 接入连接器意味着它可以在真实环境中采取真实行动。必须为每个连接器配置最小权限，高风险操作（推送代码、合并 PR、发送外部通知）应当要求人工审批，不能全自动执行。


### 要素五：子 Agent（Sub-Agents）

Loop 中最重要的架构决策之一：把写代码的 Agent 和检查代码的 Agent 分开。

写了代码的模型在评分自己的作业时会过于宽容。一个有不同指令的独立检查器——有时还使用不同的模型——能够抓住第一个 Agent 自圆其说忽略的问题。

这种"制作者-检查者"（Maker-Checker）模式也被应用到了 Loop 的停止条件上：Claude Code 的 /goal 命令在每次迭代后，会用一个单独的模型来判断是否"完成"，而不是让做了工作的那个模型来判断。


## 实例：定义检查者子 Agent


### 要素六：持久记忆（Memory）

记忆是所有能跨对话持续运行的 Loop 的核心支柱。

模型在每次对话之间会完全遗忘。如果没有外部记忆，每次 Loop 触发时 Agent 都从零开始，不知道昨天做了什么、哪些修复已经合并、哪些任务还在开放。

解决方案极其简单：把状态写在文件里，文件放在仓库里。仓库记得，即使模型不记得。


## 实例：Loop 状态文件


## 五种常见 Loop 模式

不同类型的工作任务需要不同的反馈信号和停止条件，因此发展出了几种经典的 Loop 模式。


## 构建你的第一个 Loop

不要一开始就尝试构建一个全自动、多 Agent、自动合并 PR 的复杂 Loop。从最小可用的 Loop 开始，理解它的行为后再逐步扩展。


### 第一步：从一个窄任务开始

任务越窄，Agent 越清楚哪些文件重要、哪些验证信号相关。


## 后续章节

- 第二步：明确告知验证方式
- 实例：带验证条件的 Loop 指令
- 第三步：设置保险机制
- 实例：每日 CI 故障分类 Loop（最小安全版本）
- 第四步：逐步提升自主程度
- Loop Engineering 的三大风险
- 风险一：验证仍然是你的责任
- 风险二：理解债（Comprehension Debt）积累更快
- 风险三：认知投降（Cognitive Surrender）
- 最佳实践总结

## 记忆卡片

- 一句话定义：`Loop Engineering` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
