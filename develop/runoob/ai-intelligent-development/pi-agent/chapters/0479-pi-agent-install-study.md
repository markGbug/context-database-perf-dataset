# Pi Agent：Pi Agent 安装

- 来源：[Pi Agent 安装](https://www.runoob.com/pi-agent/pi-agent-install.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：学习笔记
- 章节序号：0479

## 本章内容

本章介绍如何在不同平台上安装 Pi Agent，并完成基础环境配置。


## 环境要求

在安装 Pi Agent 之前，请确保你的系统满足以下要求：

检查 Node.js 是否已安装：

```text
node --version
```

输出类似：

```text
v20.11.0
```

查看 npm 是否同步安装（安装 Node.js 会自带）：

```text
npm --version
```

输出类似：

```text
10.2.4
```

如果你的 Node.js 版本低于 18，请先升级。可以使用 nvm（Node Version Manager）来管理多个 Node.js 版本。


## 安装


### 方式一：npm 全局安装

这是最通用、最简单的安装方式，适用于 macOS、Linux 和 Windows：

```text
# 全局安装 Pi Agent
# --ignore-scripts 禁用依赖包的生命周期脚本，提高安装安全性
npm install -g --ignore-scripts @earendil-works/pi-coding-agent
```

安装完成后验证版本:

```text
pi --version
```

安装完成后，pi 命令就可以在终端中直接使用了。


### 方式二：curl 一键脚本

在 Linux 或 macOS 上，也可以使用官方安装脚本：

```text
# 使用 curl 下载并执行安装脚本
curl -fsSL https://pi.dev/install.sh | sh
```

这个脚本会自动检测你的系统并完成安装，本质也是通过 npm 全局安装。


### 方式三：其他包管理器

如果你使用 pnpm、Yarn 或 Bun，也可以用对应的命令安装：

```text
# 使用 pnpm 安装
pnpm add -g @earendil-works/pi-coding-agent

# 使用 Yarn 安装
yarn global add @earendil-works/pi-coding-agent

# 使用 Bun 安装
bun install -g @earendil-works/pi-coding-agent
```


## 卸载方法

卸载 Pi Agent 时，请使用与你安装时相同的包管理器：

```text
# npm 或 curl 安装的用 npm 卸载
npm uninstall -g @earendil-works/pi-coding-agent

# pnpm 安装的
pnpm remove -g @earendil-works/pi-coding-agent

# Yarn 安装的
yarn global remove @earendil-works/pi-coding-agent

# Bun 安装的
bun uninstall -g @earendil-works/pi-coding-agent
```

卸载 Pi Agent 不会删除你的配置、凭证和会话记录。这些数据保存在 ~/.pi/agent/ 目录中。如需彻底清除，可以手动删除该目录。


## 终端建议

Pi Agent 使用 24 位 RGB 色彩渲染终端界面，推荐使用以下终端以获得最佳体验：

更多终端工具参考：https://www.runoob.com/w3cnote/terminal-tools.html

检查你的终端是否支持 True Color：

```text
$ echo $COLORTERM
truecolor
```

如果输出是 truecolor 或 24bit，说明你的终端支持完整的色彩渲染。


## 首次运行

安装完成后，进入一个项目目录并启动 Pi Agent：

```text
$ cd /path/to/your-project
$ pi
```

首次启动时，你会看到 Pi Agent 的欢迎界面。

此时还没有配置 AI 提供商，你需要先完成认证——这将在下一章详细说明。

Pi Agent 在启动时会以当前工作目录（cwd）作为项目根目录。它对目录中的文件拥有读写权限，建议在 git 版本控制下使用，方便随时回滚修改。


## 更新 Pi Agent

保持 Pi Agent 更新到最新版本：

```text
# 仅更新 Pi Agent 本身
pi update --self

# 更新 Pi Agent 和所有已安装的扩展包
pi update --all

# 更新模型目录（获取最新的可用模型列表）
pi update --models
```

使用 --self --force 可以强制重装 Pi Agent，即使当前已是最新版本：

```text
$ pi update --self --force
```

需要注意，通过 install.sh 等安装脚本托管的安装不支持 --force。

这类托管安装需要修复时，重新运行一次安装脚本即可。


## 复习重点

- 能说明 `Pi Agent 安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
