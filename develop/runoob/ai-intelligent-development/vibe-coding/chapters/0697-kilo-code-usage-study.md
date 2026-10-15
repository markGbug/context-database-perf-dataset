# Vibe Coding：Kilo Code 入门教程

- 来源：[Kilo Code](https://www.runoob.com/vibe-coding/kilo-code-usage.html)
- 分类：AI / 智能开发
- 技术：Vibe Coding
- 笔记类型：学习笔记
- 章节序号：0697

## 本章内容

Kilo Code 是一个开源的 AI 编程 Agent，运行在你的 VS Code、JetBrains 或命令行里，支持 500+ 个 AI 模型，目前拥有 300 万+ 开发者用户，处理了 40 万亿+ Tokens。

Kilo Code 是装在你现有 IDE（VS Code、JetBrains）里的开源 AI 编程 Agent。

Kilo Code 不是一个新的编辑器分支，不换工具、不换快捷键、不换插件——在你现有的开发环境里直接拥有 AI Agent 能力。

官方地址：https://kilo.ai/


### 与其他 AI 工具差异


## 核心特性一览

快速了解 Kilo Code 提供的主要功能能力。

- 多平台支持：VS Code、JetBrains（IntelliJ、PyCharm、WebStorm 等）、CLI、Mobile App（iOS / Android）、Slack。
- 500+ 模型，零加价：Claude、GPT、Gemini、Grok、DeepSeek、本地模型……任意切换，按模型提供商原价计费。
- 专业化 Agent 模式：Code、Ask、Plan、Debug，每种模式工具权限不同，针对不同任务优化。
- 智能补全：基于 FIM（Fill-in-the-Middle）的内联代码建议，Tab 键接受。
- 终端与浏览器控制：可以执行 Shell 命令、操控浏览器自动化。
- Checkpoints（检查点）：每次修改前自动快照，随时 /rollback 回滚。
- 并行 Agent：用 git worktrees 同时运行多个 Agent，互不干扰。
- MCP 市场：内置 MCP 服务器集成，一键连接 GitHub、数据库、Slack 等外部服务。
- 完全开源：MIT 协议，可审计、可 Fork、可定制。


## 安装

Kilo Code 支持 VS Code、JetBrains 及 CLI 等多种安装方式，下面分别介绍。


### VS Code 插件（推荐）

打开 VS Code，按 Ctrl+Shift+X（Windows/Linux）或 Cmd+Shift+X（macOS）打开插件市场。

搜索 Kilo Code，点击 安装 。

也可以从命令行安装：

```text
code --install-extension kilocode.Kilo-Code
```

安装成功后，点击右上角的 Kilo Code 图标就可以开始使用了，有一定的免费额度：

在设置页面可以定义自己的模型：


### JetBrains 插件

打开 JetBrains IDE（IntelliJ、PyCharm、WebStorm 等）。

进入 Settings → Plugins → Marketplace，搜索 Kilo Code 并安装，然后重启 IDE。


### CLI 安装（Linux/macOS）

一键安装命令：

```text
curl -fsSL https://kilo.ai/cli/install | bash
```

其他安装方式：

```text
# npm 安装
npm install -g @kilocode/cli

# Homebrew 安装（macOS/Linux）
brew install Kilo-Org/tap/kilo

# pnpm 安装
pnpm add -g @kilocode/cli

# Arch Linux (AUR) 安装
paru -S kilo-bin
```


### 其他 VS Code 兼容编辑器

Cursor、Windsurf、VSCodium、Gitpod、Eclipse Theia 等 VS Code 兼容编辑器可通过 Open VSX Registry 安装。


### 系统要求

VS Code 1.84.0 或更高版本。

Windows 用户需确保 PowerShell 已加入系统 PATH。


## 初次配置：连接模型提供商

安装插件后，打开 VS Code 侧边栏的 Kilo Code 图标，进入欢迎页开始配置。


### 方式一：注册 Kilo 账号（最快）

直接注册 app.kilo.ai 账号，创建账号后即可通过 Kilo Gateway 访问 500+ 个模型。

支持的模型包括 GPT-5.5、Claude Opus 4.7、Claude Sonnet 4.6、Gemini 3.1 Pro Preview 等，按提供商原价计费，无加价。

账号注册后会获得一定的免费额度用于体验。


### 方式二：BYOK（携带自己的 API Key）

如果你已经有某个模型提供商的 API Key，可以直接配置：

在 Kilo Code 欢迎页点击 Use your own API key。

在 Provider 下拉菜单选择你的提供商（Anthropic、OpenAI、OpenRouter、Google AI Studio 等）。

输入 API Key 并保存。

BYOK 模式完全零加价——Kilo 不从你的 Key 上赚任何差价。


### 常用提供商配置


### DeepSeek 配置

进入项目目录并执行 kilo：

```text
cd /path/to/my-project
```

在命令栏输入 /connect，打开 Connect Provider 面板，搜索 deepseek，选择 DeepSeek，然后填入你的 DeepSeek API Key。

输入 /models 打开模型选择器，选择一个可用的 DeepSeek 模型：

```text
DeepSeek V4 Flash
DeepSeek V4 Pro
```


### 最简配置：让 Agent 来做

进入插件后，直接告诉 Agent：

```text
帮我配置 OpenAI 提供商，我的 API Key 是 sk-xxxx
```

Kilo Code 内置了配置管理 skill，Agent 会自动读写 kilo.jsonc 配置文件，无需手动编辑任何配置。


## 第一次任务：5 分钟上手

通过一个简单的任务快速体验 Kilo Code 的基本工作流程。


### 打开 Kilo Code

点击 VS Code 侧边栏的 Kilo Code 图标（K 形状），打开聊天面板。


### 发送你的第一个任务

在底部输入框，用自然语言描述你想要的东西：

```text
创建一个名为 hello.txt 的文件，内容写 "Hello, Kilo!"
```

按 Enter 发送。


### 查看与审批

Kilo Code 会分析你的请求，然后提出具体操作。

默认大部分工具是自动批准的，只有执行 Shell 命令、访问外部目录、读取敏感文件时才需要你手动确认。

你会看到：

Agent 分析过程（Token 用量实时显示）。

具体操作步骤（创建哪个文件、写入什么内容）。

执行结果。


### 迭代优化

Kilo Code 是迭代式工作的，一个任务可以分多轮对话完成：

```text
第一轮：写一个 Python 函数，计算两个数的最大公约数
第二轮：加上类型注解和 docstring
第三轮：写单元测试
第四轮：重构成 class，支持多个数字的 GCD
```

每一轮 Agent 都会在前一轮的基础上继续，你不需要重新描述背景。


### 实用快捷键


## Agent 模式：选对工具做对事

Kilo Code 提供 4 个内置 Agent，每个 Agent 有不同的工具权限和行为策略。

选对 Agent，不仅效果更好，还能节省 Token 成本。


### code（默认）

定位：全能的软件工程师。

工具权限：完全访问——读文件、写文件、执行终端命令、搜索网络、调用 MCP 服务器。

适合：写代码、实现功能、Bug 修复、日常开发。

```text
切换方式：默认就是 code，或输入 /agents 选择
```


### ask

定位：只读的技术顾问。

工具权限：只读——可以读文件、运行 cat/grep/git log 等只读命令，禁止任何写操作。

适合：理解代码、解释函数逻辑、探索项目结构、学习技术概念。

```text
典型用法：
"解释这个 useEffect 的执行顺序"
"这个 SQL 查询会有性能问题吗？"
"分析整个 src 目录的架构"
```

用 ask 模式分析大型代码库，可以放心 Agent 不会误改任何文件。


### plan

定位：技术领导和系统设计师。

工具权限：只读 + 可以写 .kilo/plans/ 目录下的计划文件。

适合：系统设计、功能规划、架构决策、实施方案制定。

```text
典型用法：
"设计一个多租户 SaaS 平台的数据库架构"
"规划如何把单体应用拆分成微服务"
"在写代码之前，先给我一个分页功能的实施方案"
```

最佳实践：先用 plan 模式规划，确认方案后再切换到 code 模式实施。


## 后续章节

- debug
- 如何切换 Agent
- 中途切换模型
- 智能补全（Autocomplete）
- 工作原理
- 基本使用
- 手动触发
- 用注释引导补全
- 实例
- 补全 vs 聊天，怎么选？
- 状态栏显示
- 上下文引用：@文件和代码符号
- 文件引用
- Git 引用
- URL 引用
- 符号引用

## 复习重点

- 能说明 `Kilo Code` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
