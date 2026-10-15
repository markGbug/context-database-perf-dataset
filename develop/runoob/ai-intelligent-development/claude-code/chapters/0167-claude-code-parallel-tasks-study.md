# Claude Code：Claude Code 并行任务

- 来源：[Claude Code 并行任务](https://www.runoob.com/claude-code/claude-code-parallel-tasks.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：学习笔记
- 章节序号：0167

## 本章内容

Claude Code 提供了多种并行执行任务的机制，让你可以同时处理多个工作项，显著提升开发效率。本章将介绍三种主要的并行化方案：Subagents（子代理）、Agent Teams（代理团队）和 Git Worktree（Git 工作树），帮助你根据不同的使用场景选择最合适的方式。


## 并行任务概述

当面对复杂任务时，单个 Claude 实例可能会力不从心——上下文过长、响应变慢、任务交织。Claude Code 提供了三层并行化机制，满足不同复杂度和协作需求：

选择建议：

- 只需并行处理、相互独立的子任务 → 使用 Subagents
- 需要多个 Agent 相互讨论、协调工作 → 使用 Agent Teams
- 多个任务需要操作同一仓库的不同分支 → 使用 Git Worktree


## Subagents（子代理）


### 什么是 Subagents

Subagent 是一个独立运行的 Claude 实例，它有自己的上下文和任务焦点。主 Claude 可以创建多个 Subagent，每个 Subagent 负责一个特定的子任务：

```text
┌─────────────────────────────────────────────────────────┐
│                    主 Claude                            │
│                    (协调者)                              │
└─────────────────────────────────────────────────────────┘
                        │
                        ▼
        ┌───────────────┼───────────────┐
        ▼               ▼               ▼
┌──────────┐    ┌──────────┐    ┌──────────┐
│ Agent A  │    │ Agent B  │    │ Agent C  │
│ 代码审查  │    │ 测试生成  │    │ 文档编写  │
└──────────┘    └──────────┘    └──────────┘
        │               │               │
        └───────────────┴───────────────┘
                        │
                        ▼
                 返回结果给主代理
```

Subagent 最多可并行运行 49 个，完全满足大多数并行处理需求。


### 内置 Subagents

Claude Code 预置了以下内置 Subagent：


### 创建 Subagent

运行 /agents 命令，按提示创建新的 Subagent：

```text
/agents
```

选择 Create new agent，然后选择保存位置，描述功能后让 Claude 生成配置。

Subagent 文件使用 YAML frontmatter 进行配置，然后是 Markdown 中的系统提示：


## 实例


### Subagent 配置字段


### 控制 Subagent 能力


## 实例


## 实例


### 调用 Subagent

```text
Use the test-runner subagent to fix failing tests
```

```text
@"code-reviewer (agent)" look at the auth changes
```

```text
claude --agent code-reviewer
```


### 前台与后台运行

- 前台 Subagent：阻塞主对话直到完成
- 后台 Subagent：并发运行，可按 Ctrl+B 切换


## Agent Teams（代理团队）


### 什么是 Agent Teams

Agent Teams 可以让你协调多个 Claude Code 实例一起工作。想象一下，你同时开启 4 个 Claude 会话（ABCD），其中一个充当团队负责人（Leader），负责协调工作、分配任务并整合结果。其他三个成员各自独立工作，拥有各自的上下文窗口，同时还能直接相互沟通。


### Subagents vs Agent Teams

简单来说：Subagent 是打工人向老板汇报，Agent Teams 是平等协作的项目组。


### 启用 Agent Teams

Agent Teams 默认禁用。需要在 settings.json 中添加：


## 实例

或设置环境变量：

```text
export CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1
```

要求：Claude Code v2.1.32 或更高版本


### 启动 Agent Team

启用后，用自然语言描述任务和团队结构：


## 实例


### 控制 Agent Team

- In-process：所有队友在主终端内运行，使用 Shift+Down 循环浏览队友
- Split panes：每个队友获得自己的 tmux/iTerm2 窗格


## 实例

```text
Create a team with 4 teammates to refactor these modules in parallel.
Use Sonnet for each teammate.
```

- 负责人可显式分配任务
- 队友可自我认领未分配、未阻止的任务
- 任务有三种状态：待处理、进行中、已完成
- In-process：Shift+Down 循环浏览 → 输入消息 → Enter 查看 → Escape 中断
- Split-pane：点击队友窗格直接交互

```text
Ask the researcher teammate to shut down
```


### Agent Teams 架构

存储位置：

- Team config: ~/.claude/teams/{team-name}/config.json
- Task list: ~/.claude/tasks/{team-name}/


## Git Worktree 支持


### 问题背景

多个 Agent 同时干活时，可能会"打架"。想象一下这个场景：你让 Agent A 去重构数据库模块，让 Agent B 去修复登录页面的 bug。两个任务看起来互不相关，但它们都在同一个代码仓库、同一分支上工作。Agent A 正在修改 utils.py，Agent B 也在修改 utils.py。一个保存了一个版本，另一个覆盖了不同的版本，最终导致冲突、报错，甚至数据丢失。

这不是 AI 的问题，这是底层 Git 仓库结构的限制。


## 后续章节

- 什么是 Git Worktree
- 类比
- 使用 Git Worktree
- Subagent + Worktree 隔离
- 实例
- 使用示例
- 示例一：并行代码审查
- 使用 Subagent
- 使用 Agent Teams
- 示例二：并行研究
- 示例三：使用竞争假设进行调查
- 实例
- 示例四：多分支开发
- 示例五：链接 Subagent
- 最佳实践
- Subagent 最佳实践

## 复习重点

- 能说明 `Claude Code 并行任务` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
