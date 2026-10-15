# Ollama：Ollama 教程

- 来源：[Ollama 教程](https://www.runoob.com/ollama/ollama-tutorial.html)
- 分类：AI / 智能开发
- 技术：Ollama
- 笔记类型：练习笔记
- 章节序号：0388

## 本章内容

Ollama 是一个开源的本地大语言模型运行框架，专为在本地机器上便捷部署和运行大型语言模型（LLM）而设计。

Ollama 支持多种操作系统，包括 macOS、Windows、Linux 以及通过 Docker 容器运行。

简单来说，如果 ChatGPT、Claude、DeepSeeek 这类服务是通过互联网调用别人家的模型，那么 Ollama 更像是一个本地 AI 模型运行环境。


## 谁适合阅读本教程？

Ollama 适用于开发者、研究人员以及对数据隐私有较高要求的用户，它可以帮助用户在本地环境中快速部署和运行大型语言模型，同时提供灵活的定制化选项。

使用 Ollama，我们可以在在本地运行 qwen3.5、Llama 3.3、DeepSeek-R1、Phi-4、Mistral、Gemma 2 和其他模型。


### 开发者能用 Ollama 做什么

对开发者来说，Ollama 的价值在于把大模型变成一个可以随时调用的本地服务。

典型用途包括：AI 聊天机器人、AI 写作工具、AI 编程助手、文档分析工具、RAG 知识库、向量检索、AI Agent、自动化工作流，以及本地 AI Web 应用。

这些能力的背后，是 Ollama 提供的文本生成、聊天、模型管理、Embedding 等接口，并且支持流式响应和工具调用。


### Agent 开发者为什么需要它

如果你正在学习 Claude Code、Codex、OpenCode 等 AI 编程工具，Ollama 可以作为它们的本地模型后端。

Ollama 已经提供与 Claude Code、Codex、OpenCode、Copilot CLI、Droid 等工具的官方集成方式，一条 ollama launch 命令就能把本地模型接入这些 Agent 工作流，这部分会在集成章节详细展开。


## 学习本教程前你需要了解

Ollama 本身并不难，如果只是运行模型，基本不需要编程基础。

不同的学习目标对应的基础要求不同，可以对照下表评估自己的起点：

如果只是想体验 Ollama，知道什么是终端、命令、文件夹和模型基本就够了。

如果想进一步开发 AI 应用，建议先了解 HTTP / REST API、JSON、Python 或 JavaScript，以及 Git 和 Docker 的基本用法。


## 创建新的模型

这是 Ollama 最核心的能力：在自己电脑或服务器上运行开源模型，不需要自己搭建复杂的推理环境。

一条命令即可启动，模型运行后直接对话：

```text
ollama run qwen3.5
```

这条命令会本地启动通义千问 Qwen3.5 模型，进入交互式对话终端，如果本地没有该模型时会自动先下载，再启动。


## 相关链接

- Ollama 官方地址：https://ollama.com/
- Github 开源地址：https://github.com/ollama/ollama
- 模型列表：https://ollama.com/search
- Ollama 官方文档：https://github.com/ollama/ollama/tree/main/docs


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ollama 教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
