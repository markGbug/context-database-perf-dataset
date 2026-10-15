# Vibe Coding：Oh My Pi（omp）入门教程

- 来源：[Oh My Pi](https://www.runoob.com/vibe-coding/omp-usage.html)
- 分类：AI / 智能开发
- 技术：Vibe Coding
- 笔记类型：概念卡
- 章节序号：0698

## 本章内容

Oh My Pi（命令行简称 omp）是一个运行在终端里的开源 AI 编程 Agent，由 Can Bölük fork 自 Mario Zechner 的 Pi 并大幅扩展而来。

Oh My Pi 的核心理念是：工具不应该只是「连上去」，而要被打磨到极致——每一个工具都经过基准测试调优，编辑命中率、搜索速度、LSP 集成都力求做到同类最优。

- GitHub：https://github.com/can1357/oh-my-pi
- 官网：omp.sh


## omp 是什么？

omp 是一个终端优先的 AI 编程 Agent。它不依赖任何 IDE，在你的终端里以全功能 TUI 运行，集成了 LSP、DAP 调试器、Python/JavaScript 双执行内核、子 Agent 并行、跨会话记忆，以及一套经过基准调优的 32 个工具。


### 和其他 AI 编程工具的差异


## 安装

本节介绍 omp 在 macOS、Linux、Windows 上的多种安装方式。


### macOS / Linux（推荐）

```text
$ curl -fsSL https://omp.sh/install | sh
```

安装脚本会自动检测 Bun 是否可用：有 Bun（≥ 1.3.14）则优先用 Bun 安装，否则下载预构建二进制。


### Homebrew（macOS / Linux）

```text
$ brew install can1357/tap/omp
```


### Bun（推荐，获得最新版）

```text
$ bun install -g @oh-my-pi/pi-coding-agent
```


### Windows（PowerShell）

```text
$ irm https://omp.sh/install.ps1 | iex
```

Windows 支持原生运行，无需 WSL。


### 版本锁定（mise）

```text
$ mise use -g github:can1357/oh-my-pi
```


### 验证安装

```text
$ omp --version
```


### Shell 自动补全

omp 从 CLI 元数据动态生成补全脚本，因此子命令、Flag 和枚举值永远不会与实际 CLI 脱节：

```text
# zsh（加入 ~/.zshrc）
eval "$(omp completions zsh)"

# bash（加入 ~/.bashrc）
eval "$(omp completions bash)"

# fish
omp completions fish > ~/.config/fish/completions/omp.fish
```


### 从源码构建

```text
$ git clone https://github.com/can1357/oh-my-pi
$ cd oh-my-pi
$ bun setup    # 安装 Bun 工作区依赖并构建 Rust N-API 插件
$ bun dev      # 启动开发版 CLI

# 修改 Rust 代码后，重新构建原生插件
$ bun run build:native
```


## 初次配置：登录模型提供商

首次运行 omp 后，使用 /login 或 /model 配置你的 AI 提供商。


### 方式一：OAuth 一键登录（无需 API Key）

omp 支持多个提供商通过 OAuth 登录，最简单的方式：

```text
/login                  # 打开交互式提供商选择器
```

支持 OAuth 的提供商包括：Anthropic、OpenAI Codex、Google Antigravity（Gemini）、Perplexity、Cursor、GitHub Copilot、GitLab Duo 等。


### 方式二：API Key（直连提供商）

```text
# 在环境变量里设置（推荐写入 ~/.zshrc 或 ~/.bashrc）
export ANTHROPIC_API_KEY="sk-ant-xxxx"
export OPENAI_API_KEY="sk-xxxx"
export GOOGLE_API_KEY="xxxx"
```

或在 omp 里直接配置：

```text
/model      # 打开模型选择器，可以在这里配置 Key
```


### 方式三：Coding Plan 订阅

如果你已经订阅了 Cursor、GitHub Copilot、Kilo、Kimi Code、MiniMax Coding Plan 等服务，可以直接路由到你的订阅：

```text
/login     # 选择对应的 Coding Plan 提供商，OAuth 授权
```


### 方式四：本地模型（Ollama / LM Studio）

```text
# 先启动 Ollama
$ ollama serve

# 在 omp 里选择 Ollama 提供商（key 可选）
/model     # 选择 Ollama，指向 http://localhost:11434
```


### 配置路径

所有配置存储在 ~/.omp/ 目录：

```text
~/.omp/
  agent/
    settings.yml      # 主配置文件
    models.yml        # 自定义模型/提供商
    keybindings.yml   # 快捷键绑定
    rules/            # 流规则（stream rules）
    skills/           # 技能文档
```


## 第一次对话：TUI 基础操作

本节介绍 omp 的全屏 TUI 界面和基本交互方式。


### 启动 omp

```text
# 在项目目录下启动
$ cd ~/your-project
$ omp
```

omp 启动后进入全屏 TUI（终端用户界面），工具调用以卡片形式渲染，编辑操作在落盘前显示预览。

注意：omp 使用 Kitty 键盘协议，推荐在支持该协议的终端下运行（Kitty、Ghostty、WezTerm、iTerm2）以获得最佳体验。


### 基本交互

输入你的任务，按 Enter 发送：

```text
> 分析这个项目的目录结构，告诉我主要模块是什么
```

omp 会自动调用 read、search 等工具扫描代码库，返回结构化摘要。


### 常用键位


### 单次执行（非交互模式）

```text
# 一次性执行任务并退出
$ omp -p "列出所有 .ts 文件里未使用的 export"

# 管道输入
$ git diff HEAD~1 | omp -p "给这个 diff 写一个精简的 commit message"
```


### 恢复历史会话

```html
$ omp --resume          # 打开会话选择器（Tab 补全可用）
$ omp --resume <id>     # 直接恢复指定会话
```


## 核心工具详解

omp 的 32 个工具统一在一个命名空间里，read、search、bash 是日常使用最频繁的三个。


## 后续章节

- read：统一读取接口
- search：in-process ripgrep
- edit：Hashline 精确编辑
- bash：持久 Shell 会话
- eval：Python + JavaScript 持久内核
- lsp：完整 LSP 操作
- todo：任务管理
- ask：结构化问题
- Hashline：更精准的文件编辑
- 传统 str_replace 的问题
- Hashline 的解法
- 基准测试结果
- ast_edit：结构化代码重写
- ast_grep：结构化代码查询
- LSP 集成：IDE 知道的，Agent 也知道
- 配置 LSP 服务器

## 记忆卡片

- 一句话定义：`Oh My Pi` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
