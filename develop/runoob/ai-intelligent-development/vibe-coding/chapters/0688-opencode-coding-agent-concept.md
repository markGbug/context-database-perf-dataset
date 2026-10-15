# Vibe Coding：OpenCode 入门教程

- 来源：[OpenCode 入门教程](https://www.runoob.com/vibe-coding/opencode-coding-agent.html)
- 分类：AI / 智能开发
- 技术：Vibe Coding
- 笔记类型：概念卡
- 章节序号：0688

## 本章内容

OpenCode 是一个开源的 AI 编程代理（AI coding agent），支持在终端（Terminal）、桌面应用和主流 IDE（如 VS Code）中与 AI 交互完成代码相关任务。

OpenCode 可以帮助我们理解代码库、编写新功能、重构代码、修复 Bug 等，大幅提升开发效率。

OpenCode 类似于 Claude 的 Code 模式或 Cursor 的 Agent 功能，但完全开源、隐私优先，支持多种大语言模型（LLM），并强调终端体验。

OpenCode 支持 75+ 家模型提供商，内置 GLM-4.7、MiniMax M2.1 等免费模型，可对接 OpenAI、Anthropic、Google 等商业模型，也能配置本地模型（如 Llama 3），按需适配轻量脚本、复杂架构等不同场景。

OpenCode 完整教程参考：https://www.runoob.com/opencode/opencode-tutorial.html


### 关键特性

两种内置 Agent 模式：

- Build 模式：全权限，可直接编辑文件、执行命令。
- Plan 模式：只读规划，默认拒绝编辑，需要确认。

工具集：bash 执行、文件读写、grep 搜索、LSP 诊断等。

上下文感知：自动分析项目结构，生成 AGENTS.md 指南。

分享与协作：一键生成会话分享链接。


## 安装 OpenCode

OpenCode 支持 macOS / Windows / Linux 多平台安装。

通用一键安装脚本这是最简单的方法：

```text
curl -fsSL https://opencode.ai/install | bash
```

安装完成后，你应该能通过命令行运行：

```text
opencode --version
```

如果输出类似 1.1.19 这种的版本号信息表示安装成功。


## 记忆卡片

- 一句话定义：`OpenCode 入门教程` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
