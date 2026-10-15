# Pi Agent：Pi Agent 简介

- 来源：[Pi Agent 简介](https://www.runoob.com/pi-agent/pi-agent-intro.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：练习笔记
- 章节序号：0477

## 本章内容

Pi Agent（全称 Pi Coding Agent，下文简称 Pi）是一个极简的终端 AI 编程助手，在命令行界面中通过自然语言对话帮你完成编码任务。

Pi Agent 由 earendil-works 团队开发，核心代码保持精简，同时通过可扩展的插件体系支持各种工作流。

Pi 是一个运行在终端里的 AI 编码 Agent，类似于 Claude Code、OpenAI Codex CLI 这类工具。

Pi 的官方理念是："There are many agent harnesses but this one is yours"（Agent 工具很多，但这个是你自己的）。


## 什么是 Pi Agent

Pi Agent 是一个运行在终端（Terminal）中的编程助手。

你可以在项目目录中启动它，用自然语言描述需求，它会读取你的代码、执行命令、修改文件，像一个协作开发者一样工作。

它的核心设计原则是：核心保持最小化，工作流相关的功能通过 Extensions（扩展）、Skills（技能）、Prompt Templates（提示词模板）和 Themes（主题）来实现，而不是内置到核心中。

Pi Agent 有意不内置 MCP、子代理（sub-agent）、权限弹窗、Plan 模式、待办事项（to-dos）和后台 Bash 等功能。

如果你需要这些工作流，可以通过扩展或包来安装。


## Pi Agent 与其他工具的区别

Pi Agent 的定位与以下工具类似但又有所不同：


## 核心特性一览

Pi Agent 的核心特性覆盖运行模式、提供商接入、内置工具、扩展体系和主题定制，足以支撑日常的终端编程工作。


## 适用场景

Pi Agent 适合以下使用场景：

Pi Agent 是面向开发者的工具，假设你已经熟悉命令行操作。

如果你之前没有在终端中工作的经验，可以先花一些时间熟悉基础的 shell 操作。


## 设计哲学

Pi Agent 的核心理念是：不做大而全，而是提供可组合的基础能力。

它的创作者认为，过多的内置功能会让工具变得臃肿且难以维护。

因此 Pi Agent 将核心限定在最小的可用范围内，其余能力交由扩展系统完成。

这种设计的好处包括：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pi Agent 简介` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
