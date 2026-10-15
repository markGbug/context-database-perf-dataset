# AI Agent（智能体）：Deep Agents 入门教程

- 来源：[Deep Agents 入门教程](https://www.runoob.com/ai-agent/deep-agents-usage.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：练习笔记
- 章节序号：0025

## 本章内容

Deep Agents 是 LangChain 官方推出的一套开箱即用（Batteries Included）的 Agent 开发框架，专门面向复杂任务、长流程执行、多步骤规划以及多 Agent 协作场景而设计。

相比传统 Agent 需要开发者自行组合 Prompt、Tool、Memory、Workflow 等组件，Deep Agents 已经内置了任务规划、文件系统、子 Agent 调度、上下文压缩、记忆管理等核心能力，让开发者能够将更多精力放在业务逻辑上，而不是底层架构搭建。

本教程面向零基础开发者，带你从安装配置开始，逐步了解 Deep Agents 的核心工作机制，并使用 DeepSeek API 构建一个真实可运行的 AI Agent 项目。


## 什么是 Deep Agents

Deep Agents 可以理解为一个面向生产环境的高级 Agent 框架（Agent Harness）。

官方将其定义为：一个具备完整基础设施的 Agent 运行框架，而不仅仅是一个简单的 LLM + Tool 调用循环。

安装完成后，即可直接获得以下能力，无需额外开发：

- 自动任务规划（Planning）
- 文件系统读写（Filesystem）
- 子 Agent 协作（Sub Agents）
- 上下文压缩与管理（Context Management）
- 长任务执行（Long Running Tasks）
- 人工审批（Human-in-the-Loop）
- 持久化记忆（Memory）
- 流式输出（Streaming）


### Deep Agents 的设计目标

传统 Agent 通常采用 ReAct 模式：用户输入 → LLM 推理 → 调用工具 → LLM 推理 → 调用工具 → 输出结果。

当任务规模较小时，这种模式运行良好。但随着任务复杂度提升（例如自动生成市场调研报告、分析多家公司财报、编写完整项目代码），就会逐渐暴露出以下问题：

- 上下文窗口迅速膨胀，超出模型限制
- 推理链过长导致性能下降
- Agent 容易遗忘之前完成的工作
- 多任务之间缺乏隔离，相互干扰
- Tool 调用逻辑越来越复杂，难以维护

Deep Agents 的核心目标，就是解决这些复杂任务场景下的工程化问题。


### 与 LangChain、LangGraph 的关系

很多初学者容易混淆这三个项目的定位，它们实际上处于不同的抽象层级。

三者并非相互替代，而是可以协同使用：LangChain 提供积木，LangGraph 是组织积木的工程框架，Deep Agents 是在此之上开箱即用的高级应用层。任何一个 LangGraph CompiledStateGraph 都可以作为 subagent 传入 Deep Agents，三层可以灵活混用。


### 核心能力一览

Deep Agents 内置以下中间件，无需额外配置即可使用：


## 安装

Deep Agents 发布在 PyPI，包名为 deepagents。

推荐使用 uv 安装，速度更快；也可以使用传统的 pip。


### 使用 uv 安装（推荐）

```text
uv init
uv add deepagents tavily-python
uv sync
```


### 使用 pip 安装

```text
pip install deepagents tavily-python
```


### 搭配 DeepSeek API 安装

DeepSeek 兼容 OpenAI 接口，因此需要同时安装 langchain-openai。

```text
pip install deepagents langchain-openai
```

Deep Agents 对模型的唯一要求是：该模型支持 tool calling（工具调用）。DeepSeek V3 和 DeepSeek R1 系列均支持，可放心使用。


## 配置说明

create_deep_agent 是创建 Agent 的核心函数，支持以下参数配置。


### 文件系统后端对比

Deep Agents 提供多种后端，用来控制 Agent 如何读写文件。

初学者直接使用默认的 StateBackend 即可。FilesystemBackend 和 LocalShellBackend 会让 Agent 直接操作你的本地文件系统，需要严格配置权限后再使用。


## 快速开始

本节演示如何用最少的代码创建一个可以运行的 Deep Agent。


### 配置 DeepSeek API Key

DeepSeek 兼容 OpenAI 的接口格式，需要同时设置 API Key 和 Base URL。

```text
export OPENAI_API_KEY="sk-your-deepseek-api-key"
export OPENAI_BASE_URL="https://api.deepseek.com"
export TAVILY_API_KEY="your-tavily-api-key"
```

DeepSeek 的 API Key 可在 platform.deepseek.com 申请。将环境变量 OPENAI_BASE_URL 指向 DeepSeek 的地址，LangChain 会自动将请求转发过去。

TAVILY_API_KEY 需要到 Tavily 官方网站 https://www.tavily.com/ 申请，生成的 tvly-xxxxxxxx 格式密钥。


### 最简示例：Hello World Agent

创建一个带自定义工具的 Agent，向 DeepSeek 发送第一条消息。


## 实例

```text
# 运行脚本
python hello_agent.py
```

北京今天**晴天**，气温 **25°C**，非常适合出行。☀️

注意：Agent 返回的是完整的消息列表（messages），最终回复位于列表末尾，即 result["messages"][-1].content。


## 详细用法

本节通过几个真实场景，逐步展示 Deep Agents 的核心能力。


### 使用 DeepSeek R1 进行推理任务

DeepSeek R1 是推理增强模型，适合需要复杂分析的任务。


## 实例

执行输出：

```text
再换一种方法做交叉验证：

- 1 到 100 所有整数之和：\( \frac{100 \times 101}{2} = 5050 \)
- 1 到 100 的偶数之和：\( 2 + 4 + \cdots + 100 = 2 \times \frac{50 \times 51}{2} = 2550 \)
- 奇数之和：\( 5050 - 2550 = 2500 \)

两种方法结果一致。

---

**结论**：1 到 100 的所有奇数之和为 **2500**。

**推导回顾**：
- 奇数序列首项 1，末项 99，项数 \( \frac{99-1}{2}+1 = 50 \)
- 等差数列求和：\( S = \frac{n(a_1 + a_n)}{2} = \frac{50 \times (1+99)}{2} = 2500 \)
```


### 自定义系统提示词

通过 system_prompt 参数定义 Agent 的角色、任务目标和行为规范。


## 实例


### 流式输出

对于需要实时展示进度的场景，可以使用 stream 方法逐块接收 Agent 输出。


## 实例


### 多轮对话（带检查点）

配合 MemorySaver 检查点，可以实现跨轮次的有状态对话。


## 实例

```text
第一轮回复：你好，RUNOOB！很高兴认识你，Python 是一门非常适合初学者的语言...
第二轮回复：你叫 RUNOOB，你正在学习 Python！...
```

thread_id 的作用：同一个 thread_id 下的所有调用共享同一段对话历史。不同的 thread_id 之间相互隔离，互不干扰。可以把它理解为"对话房间号"。


## 综合 Demo：研究报告 Agent

本节展示一个完整的研究报告 Agent，使用 DeepSeek V3 作为主模型，集成自定义搜索工具，并演示子 Agent 的使用。


## 后续章节

- 场景说明
- 实例
- Human-in-the-loop 示例
- 实例
- 常见问题
- 如何判断选用 Deep Agents 还是直接用 LangChain/LangGraph？
- DeepSeek 模型的选择建议
- Agent 调用工具后没有返回结果怎么办？
- 如何让 Agent 一次只能访问特定文件？
- 实例
- Agent 默认系统提示词和我的提示词如何合并？
- 初学者容易犯的错误
- 更多资料

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Deep Agents 入门教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
