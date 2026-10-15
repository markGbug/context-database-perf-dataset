# Claude Code：Claude Code 安装与使用

- 来源：[Claude Code 安装与使用](https://www.runoob.com/claude-code/claude-code-install.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：学习笔记
- 章节序号：0135

## 本章内容

在正式安装之前，先了解一下 Claude Code 有哪几种使用方式，选择最适合自己的方式入手。

选择建议：

- 如果你是完全新手，先访问 https://claude.ai/ 用 Web 端试试手感，熟悉 Claude 的对话方式
- 如果你想真正用于开发，直接学习 CLI（命令行），功能最完整
- 等 CLI 用熟之后，再根据需要考虑编辑器集成

目前 Claude Code 也提供了桌面版，可在以下地址下载：https://claude.com/download

本教程以 CLI 方式为主，因为它最稳定、最通用，也最接近 Claude Code 的设计初衷。


## 安装 Claude Code CLI


### 1、前置准备

在安装之前，你需要准备好以下两项：

① Claude 账号

- 访问 claude.ai 注册一个账号
- 如果你已经在使用 Claude 网页版聊天，说明账号已经有了，可以跳过这步
- 如果你打算使用国内大模型（如 DeepSeek、Minimax、GLM 等），可以暂时跳过账号注册，后文会介绍如何切换

② 命令行工具

- Mac / Linux：打开系统自带的 Terminal（终端）即可
- Windows：打开 PowerShell，或者安装并使用 WSL（Windows Subsystem for Linux）


### 2、使用官方脚本安装（推荐）

官方提供了一键安装脚本，根据你的系统选择对应的命令执行：

macOS、Linux、WSL：

```text
curl -fsSL https://claude.ai/install.sh | bash
```

Windows PowerShell：

```text
irm https://claude.ai/install.ps1 | iex
```

Windows CMD：

```text
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
```

Homebrew:

```text
brew install --cask claude-code
```

WinGet:

```text
winget install Anthropic.ClaudeCode
```

安装完成后，验证是否安装成功：

```text
claude --version
```

如果终端输出了版本号（如 1.x.x），说明安装成功:

```text
2.1.81 (Claude Code)
```


### 3、使用 npm 安装（不推荐）

官方目前已不再推荐使用 npm 安装方式，建议优先使用上方的官方脚本。如果确实需要通过 npm 安装，请先确认已安装 Node.js：

```text
node --version
```

如果输出了版本号（如 v18.17.0），说明已安装。如果提示命令不存在，请前往 nodejs.org 下载并安装。

确认 Node.js 可用后，执行以下命令安装 Claude Code：

```text
npm install -g @anthropic-ai/claude-code
```

等待安装完成（可能需要几分钟），然后验证：

```text
claude --version
```


### 4、更新 Claude Code

可以直接用以下命令更新：

```text
claude install
```

或者：

```text
claude update
```

Claude Code 在启动和运行时会自动检查更新，后台下载完成后，下次启动即生效。自动更新相关配置写在 settings.json 中：


## 实例

也可以在 Claude Code 内部通过 /config 命令进行配置。

如果你不需要自动更新，可以在 settings.json 的 env 中禁用：


## 实例

通过 Homebrew 或 WinGet 安装的 Claude Code 不支持自动更新，需要手动执行以下命令更新：

```text
# macOS Homebrew
brew upgrade claude-code

#Windows WinGet
winget upgrade Anthropic.ClaudeCode
```


### 5、常见安装问题排查

问题一：提示 npm command not found

- 原因：电脑上没有安装 Node.js
- 解决：前往 nodejs.org 下载安装 Node.js，安装完成后重新执行安装命令

问题二：提示 permission denied

- 原因：当前用户没有全局安装权限
- 解决（Mac / Linux）：在命令前加 sudo 提升权限： sudo npm install -g @anthropic-ai/claude-code
- 解决（Windows）：右键 PowerShell，选择"以管理员身份运行"，然后重新执行安装命令

问题三：安装速度很慢或卡住

- 原因：网络访问境外源速度慢
- 解决：添加 --registry 参数切换到国内镜像源： npm install -g @anthropic-ai/claude-code --registry=https://registry.npmmirror.com

终端推荐：如果你觉得系统默认终端体验一般，以下这些终端在使用 Claude Code 时体验更佳：

- WezTerm（跨平台）：https://wezterm.org/
- Alacritty（跨平台）：https://alacritty.org/
- Ghostty（Linux / macOS）：https://ghostty.org/
- Kitty（Linux / macOS）：https://github.com/kovidgoyal/kitty

更多终端工具参考：https://www.runoob.com/w3cnote/terminal-tools.html


## 卸载 Claude Code

根据你当初的安装方式选择对应的卸载命令。


### 1、官方脚本安装（原生安装）

删除 Claude Code 的可执行文件和版本文件：

macOS、Linux、WSL：

```text
rm -f ~/.local/bin/claude
rm -rf ~/.local/share/claude
```

Windows PowerShell：

```text
Remove-Item -Path "$env:USERPROFILE\.local\bin\claude.exe" -Force
Remove-Item -Path "$env:USERPROFILE\.local\share\claude" -Recurse -Force
```


### 2、Homebrew 安装

```text
brew uninstall --cask claude-code
```


### 3、WinGet 安装

```text
winget uninstall Anthropic.ClaudeCode
```


### 4、npm 安装

```text
npm uninstall -g @anthropic-ai/claude-code
```


### 5、删除配置文件（可选）

以上命令只卸载了可执行程序，配置文件和历史记录不会自动删除。如果你希望完全清除所有数据（包括设置、授权工具、MCP 服务器配置和会话历史），需要额外执行以下命令：

⚠️ 删除配置文件是不可恢复的操作，所有本地设置和历史记录将永久丢失，执行前请确认。

macOS、Linux、WSL：

```text
# 删除全局用户设置和状态
rm -rf ~/.claude
rm ~/.claude.json

# 删除当前项目的本地设置（在项目目录中执行）
rm -rf .claude
rm -f .mcp.json
```

Windows PowerShell：

```text
# 删除全局用户设置和状态
Remove-Item -Path "$env:USERPROFILE\.claude" -Recurse -Force
Remove-Item -Path "$env:USERPROFILE\.claude.json" -Force

# 删除当前项目的本地设置（在项目目录中执行）
Remove-Item -Path ".claude" -Recurse -Force
Remove-Item -Path ".mcp.json" -Force
```


## 登录 Claude Code


### 1、首次登录流程

在项目目录中启动 Claude Code：

```text
claude
```

首次启动时，Claude Code 会引导你完成登录。你也可以在进入界面后手动输入登录命令：

```text
/login
```

按照终端中的提示完成登录授权即可。登录后，凭据会保存在本地，下次启动无需重复登录。如果需要切换账号，重新执行 /login 即可。


### 2、支持的账号类型

你可以使用以下任意一种账号类型登录：

- Claude Pro：个人专业版
- Claude Max：最高级别订阅
- Claude Teams：团队版
- Claude Enterprise：企业版
- 通过 API 访问，使用预付费积分计费
- 适合开发者和需要程序化访问的场景
- 同一个邮箱可以同时拥有订阅账号和 Console 账号两种类型


### 3、自动创建工作区（Console 账号）

首次使用 Claude Console 账号认证 Claude Code 时，系统会自动在你的 Console 中创建一个名为 "Claude Code" 的工作区，用于：

- 集中跟踪所有 Claude Code 的 API 使用成本
- 便于管理组织内多人的 Claude Code 使用情况


## 启动第一次会话


### 1、在项目目录中启动

打开终端，先切换到你的项目目录，再启动 Claude Code。这样 Claude 才能读取你的项目文件，提供针对性的帮助：

```text
cd /path/to/your/project
claude
```


### 2、欢迎界面

启动后，你会看到 Claude Code 的欢迎界面，包括当前会话信息、最近的对话记录和最新更新说明：


### 3、查看可用命令

在输入框中输入 /help 可以查看所有可用功能：

```text
/help
```

输入 /resume 可以恢复之前中断的对话：

```text
/resume
```

在输入框中直接输入 /，会弹出所有可用命令的补全列表：

详细的凭据管理信息可参考官方文档的 Credential Management 部分。


## 提出第一个问题


### 1、理解项目

进入项目目录启动 Claude Code 后，可以先让它分析你的代码库：

```text
what does this project do?
```

Claude 会自动读取项目文件，并给出项目概要。

Claude Code 会根据需要自动读取文件——你不需要手动把文件内容复制粘贴到对话中，它会自己找到需要的上下文。


## 后续章节

- 2、更多项目相关问题
- 3、询问 Claude Code 的能力
- 进行第一次代码修改
- 1、动手试一个简单任务
- 2、Claude Code 的修改工作流
- 使用 Git 功能
- 1、基础 Git 操作
- 2、更复杂的 Git 操作
- 修复 Bug 或添加功能
- 1、添加新功能
- 2、修复现有问题
- 3、Claude Code 的问题处理流程
- 其他常见工作流
- 代码重构
- 编写测试
- 更新文档

## 复习重点

- 能说明 `Claude Code 安装与使用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
