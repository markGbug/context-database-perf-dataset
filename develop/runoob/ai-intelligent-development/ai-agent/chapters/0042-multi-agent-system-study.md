# AI Agent（智能体）：多智能体系统（Multi-Agent System）

- 来源：[多智能体系统](https://www.runoob.com/ai-agent/multi-agent-system.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：学习笔记
- 章节序号：0042

## 本章内容

本章节介绍多智能体系统（Multi-Agent System）。

多智能体系统通过多个 Agent 的协作来完成复杂任务。

这是构建大规模 AI 系统的关键技术，能够实现单一 Agent 无法完成的复杂功能。


## 多 Agent 架构基础

多 Agent 系统的核心挑战包括三个方面。

分工问题：如何将任务合理分配给不同的 Agent。

通信问题：Agent 之间如何传递信息。

协调问题：如何确保多个 Agent 的行动一致且高效。


### 基本架构模式

层次架构采用树状结构，有一个主 Agent 负责调度。

主 Agent（Orchestrator）负责任务分解和结果整合。

从 Agent（Subagent）负责执行具体任务。

```text
Orchestrator (调度者)
    |
    +-- Agent A (专家A)
    +-- Agent B (专家B)
    +-- Agent C (专家C)
```

平级架构中所有 Agent 地位平等，直接通信协作。

适合 Agent 之间需要频繁对等交互的场景。

```text
Agent A <--> Agent B
    |           |
    v           v
Agent C <--> Agent D
```


## 角色分工与协作

有效的多 Agent 系统需要明确的角色定义。

每个 Agent 应该有自己的专长和职责范围。

协作机制确保多个 Agent 能够协调工作。


### 常见角色定义

规划者（Planner）：分解复杂任务，制定执行计划。

执行者（Executor）：调用工具，执行具体操作。

审核者（Reviewer）：评估结果，提出改进建议。

协调者（Coordinator）：管理 Agent 间的通信和任务分配。


### 代码实现


## 多 Agent 系统基础实现


## AutoGen 框架

AutoGen 是微软开发的多 Agent 编程框架。

它提供了一套简洁的 API 来构建多 Agent 对话系统。

AutoGen 大大简化了多 Agent 系统的开发复杂度。


### 核心概念

AssistantAgent：能够调用工具的智能助手 Agent。

UserProxyAgent：代表用户行为，可以执行代码和工具调用。

GroupChat：支持多个 Agent 之间的群聊协作。

GroupChatManager：管理群聊中的 Agent 交互。


### 代码示例


## AutoGen 基本使用


### 更复杂的 AutoGen 示例


## AutoGen 工具调用


## A2A 与 MCP 协议

多 Agent 系统需要标准化的通信协议。

A2A 和 MCP 是两个重要的协议标准。


### A2A（Agent-to-Agent）协议

A2A 协议定义了 Agent 之间通信的标准格式。

它支持代理发现、任务协作和状态同步。

代理发现（Agent Discovery）：Agent 能够发现其他 Agent 的能力和服务。

任务协作（Task Collaboration）：多个 Agent 能够协同完成复杂任务。

状态同步（State Synchronization）：Agent 之间能够同步状态信息。


### MCP（Model Context Protocol）协议

MCP 是一种开放标准协议。

使得 AI 模型能够安全地与外部工具和数据源连接。

MCP 是工具接入的标准协议，类似于 USB 接口的作用。

Host：运行 AI 应用的宿主环境。

Client：与 MCP 服务器建立连接的客户端。

Server：提供工具和资源的服务端。


## MCP 工具定义

注意：A2A 和 MCP 解决的问题不同。A2A 解决的是 Agent 之间的通信问题，MCP 解决的是 Agent 与外部工具的连接问题。两者可以结合使用，构建完整的多 Agent 系统。


## 主从 Agent 模式

主从模式是一种经典的多 Agent 架构模式。

主 Agent（Orchestrator）负责任务分解和结果整合。

从 Agent（Subagent）负责执行具体任务。


### 适用场景

任务可以清晰地分解为独立子任务的场景。

需要不同专业技能的 Agent 协作完成的场景。

需要中央协调和控制的复杂工作流。


### 代码实现


## 主从 Agent 模式实现


### 主从模式的优缺点


## 章节小结

本章节介绍了多智能体系统的核心概念和实现方法。

多 Agent 架构基础 介绍了层次架构和平级架构两种基本模式。

角色分工与协作 通过明确的角色定义提高系统效率。

AutoGen 框架 提供了简化多 Agent 开发的编程框架。

A2A 和 MCP 协议 是 Agent 通信和工具接入的标准协议。

主从 Agent 模式 适合有明确层次结构的复杂任务。

选择合适的多 Agent 架构需要根据具体场景。

对于简单场景，单个 Agent 即可满足需求。

对于复杂场景，需要根据任务特点选择合适的架构模式。


## 复习重点

- 能说明 `多智能体系统` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
