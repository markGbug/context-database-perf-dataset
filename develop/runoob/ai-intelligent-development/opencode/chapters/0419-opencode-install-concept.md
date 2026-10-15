# OpenCode：OpenCode 安装

- 来源：[OpenCode 安装](https://www.runoob.com/opencode/opencode-install.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：概念卡
- 章节序号：0419

## 本章内容

OpenCode 是一个开源的 AI 编程 Agent，支持在终端中直接完成代码理解、修改、执行等开发任务。

相比传统 AI 工具，OpenCode 可以直接参与开发流程，而不仅仅是生成代码。

在安装之前，需要确保你的环境满足以下条件：


### 1、操作系统要求

- macOS
- Linux
- Windows（推荐使用 WSL）


### 2、终端工具

需要一个现代终端，例如：

- WezTerm（跨平台）：https://wezterm.org/
- Alacritty（跨平台）：https://alacritty.org/
- Ghostty（Linux/macOS）：https://ghostty.org/
- Kitty（Linux/macOS）：https://github.com/kovidgoyal/kitty

更多终端工具参考：https://www.runoob.com/w3cnote/terminal-tools.html


### 3、API Key

OpenCode 本身不提供模型，需要你配置 AI 服务商（后文会详细介绍）：

- OpenAI（GPT）
- Anthropic（Claude）
- Google（Gemini）
- DeepSeek
- 阿里百炼
- GLM
- MiniMax


## 安装方式

OpenCode 提供多种安装方式，推荐优先使用官方脚本。


## 1、一键安装（推荐）

```text
curl -fsSL https://opencode.ai/install | bash
```

说明：

- 自动下载最新版本
- 自动配置环境
- 适用于 macOS / Linux / WSL

安装完成后，还会提示你怎么用，OpenCode 包含免费模式，使用方式：

```html
cd <project>  # 进入项目目录
opencode      # 启动 OpenCode
```


### 2、使用 Node.js 安装

如果你熟悉 Node.js，可以使用：

```text
npm install -g opencode-ai
```

或者：

```text
pnpm install -g opencode-ai
```

或者：

```text
yarn global add opencode-ai
```


### 3、macOS（Homebrew）

```text
brew install anomalyco/tap/opencode
```

说明：

- 推荐使用官方 tap（更新更快）
- brew install opencode 更新较慢


### 3、Windows 安装


### 推荐方式：WSL

原因：

- 更稳定
- 完整支持所有功能

使用 Chocolatey：

```text
choco install opencode
```

使用 Scoop：

```text
scoop install opencode
```

使用 NPM：

```text
npm install -g opencode-ai
```

使用 Mise：

```text
mise use -g github:anomalyco/opencode
```

使用 Docker：

```text
docker run -it --rm ghcr.io/anomalyco/opencode
```

你也可以从 Releases 页面 https://github.com/anomalyco/opencode/releases 直接下载二进制文件。


### 4、Linux 安装

通用方式（推荐）：

```text
curl -fsSL https://opencode.ai/install | bash
```

Arch Linux：

```text
sudo pacman -S opencode
```

或：

```text
paru -S opencode-bin
```

Docker（进阶）：

```text
docker run -it --rm ghcr.io/anomalyco/opencode
```


## 验证安装

安装完成后，执行：

```text
opencode --version
```

如果输出类似：

```text
1.1.50
```

说明安装成功。


## 启动 OpenCode

直接运行：

```text
opencode
```

如果出现 EACCES: permission denied, open '' 是权限问题，我们可以修复目录权限：

```text
sudo chown -R $(whoami) ~/.local
```

然后执行：

```text
chmod -R 755 ~/.local
```

你会看到终端界面（TUI）:

打开后，你就可以在这个界面提问了。


## 记忆卡片

- 一句话定义：`OpenCode 安装` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
