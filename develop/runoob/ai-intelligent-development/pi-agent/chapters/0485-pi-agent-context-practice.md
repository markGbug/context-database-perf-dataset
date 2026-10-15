# Pi Agent：Pi Agent 上下文管理

- 来源：[PI Agent 上下文管理](https://www.runoob.com/pi-agent/pi-agent-context.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：练习笔记
- 章节序号：0485

## 本章内容

上下文管理是高效使用 Pi Agent 的核心技能。

本章介绍如何通过环境文件控制 AI 的行为，以及如何管理对话上下文。


## 上下文文件概述

Pi Agent 在启动时会自动加载项目指令文件，让 AI 了解你的项目规范、命令和偏好。

这些文件告诉 AI「在这个项目中应该怎样工作」。


## AGENTS.md / CLAUDE.md

这是 Pi Agent 最重要的上下文文件，加载顺序为：

- ~/.pi/agent/AGENTS.md - 全局指令，对所有项目生效
- 从当前目录向上遍历各级父目录中的 AGENTS.md 或 CLAUDE.md
- 当前目录下的 AGENTS.md 或 CLAUDE.md

以下是一个放在项目根目录 AGENTS.md 中的完整示例：


## 实例

更新 AGENTS.md 后，使用 /reload 命令即可热重载，无需重启 Pi Agent。

如果你同时有 AGENTS.md 和 CLAUDE.md，Pi Agent 会优先加载 AGENTS.md。

如果你之前使用 Claude Code，可以直接复用已有的 CLAUDE.md。

若目录中存在 AGENTS.override.md，它会取代该目录的 AGENTS.md 与 CLAUDE.md 被加载。

如果想禁用上下文文件加载，使用命令行参数：

```text
$ pi --no-context-files
$ pi -nc   # 短形式
```


## SYSTEM.md

SYSTEM.md 用于完全替换 Pi Agent 的默认系统提示词，只想追加内容时则改用 APPEND_SYSTEM.md。

两者都分全局与项目两级，路径与作用如下：

大多数情况下你不需要修改系统提示词。

AGENTS.md 已经能覆盖绝大部分的定制需求。

SYSTEM.md 适用于需要深度定制 AI 行为的场景，修改不当可能影响 AI 的工作效果。


## 上下文压缩（Compaction）

当对话变得很长时，AI 的上下文窗口（context window）会逐渐被占满。

Pi Agent 通过上下文压缩（Compaction）来解决这个问题——它会自动将较早的对话内容总结为简短的摘要，释放上下文空间。


### 自动压缩

默认情况下，Pi Agent 会在上下文接近模型限制时自动触发压缩。

压缩行为由 ~/.pi/agent/settings.json 中的 compaction 配置控制：


## 实例

触发条件是上下文 token 超过 contextWindow 减去 reserveTokens 后的可用空间。

检查时机在每次工具执行完毕之后、下一条用户提示发送之前。


### 手动压缩

你也可以随时手动触发压缩：

```text
/compact
```

压缩时可以添加自定义指令，告诉 AI 在总结时关注哪些内容：

```text
/compact 重点关注错误修复和 API 变更
```

压缩只对当前对话上下文不可逆。

被压缩的原始消息仍完整保留在会话文件中，用 /tree 跳回压缩前的节点即可找回细节。

如果想在压缩前留一份完整备份，推荐使用 /clone。

/clone 会完整复制当前活动分支到新会话文件，适合压缩前备份。

/fork 只从某条历史用户消息起算，其后内容不会带入新会话。


## 推理过程显示

支持推理输出的模型在回答之前会进行思考。

你可以通过以下设置控制推理过程的显示：

使用 Ctrl+T 可以在对话过程中随时切换推理过程的显示/隐藏。


## 热重载（/reload）

修改配置后是否需要重启，取决于你改了什么。

下表汇总了常见变更的生效方式，标记为「否」的项目执行 /reload 即可：


## 上下文使用量查看

底部状态栏会实时显示当前上下文的 token 用量和费用。

使用 /session 命令可以查看更详细的信息：

```text
/session
```

输出示例：

```text
Session file: ~/.pi/agent/sessions/--Users-runoob-projects-runoob-demo--/2026-08-30T09-15-04-000Z_019fbb5d-7a2e-7f31-b5c4-1a2b3c4d5e6f.jsonl
Session ID:   abc123-def456
Messages:     42
Tokens:       85,432
Cost:         $0.52
Current model: claude-sonnet-4-20250514
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PI Agent 上下文管理` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
