# Pi Agent：Pi Agent 多平台部署

- 来源：[Pi Agent 多平台部署](https://www.runoob.com/pi-agent/pi-agent-platforms.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：学习笔记
- 章节序号：0498

## 本章内容

Pi Agent 支持在 Windows、macOS、Linux 和 Android（Termux）上运行。

本章介绍各平台的配置要点。


## macOS 配置

macOS 是 Pi Agent 的一等支持平台，大部分功能开箱即用。


### 推荐终端


### 验证 True Color 支持

```text
$ echo $COLORTERM
truecolor
```


### Shell 别名

Pi Agent 在非交互模式下运行 bash（即 bash -c）时，默认不会自动展开你的 Shell 别名。

核心机制：让 Pi 识别 Shell 别名若要在 Pi 中使用自定义别名，需将以下配置写入 ~/.pi/agent/settings.json（或 ~/.atomic/agent/settings.json）中，令其在启动时主动加载你的 Shell 配置文件（如 ~/.zshrc 或 ~/.bashrc）：

```text
{
  "shellCommandPrefix": "shopt -s expand_aliases\neval \"$(grep '^alias ' ~/.zshrc)\""
}
```

注意：请把路径 ~/.zshrc 改成你实际使用的 Shell 配置文件路径。


## Windows 配置

Windows 上可以通过原生终端或 WSL2 运行 Pi Agent，关键是选对终端并处理快捷键冲突。


### 推荐安装方式

在 Windows 上推荐使用 Windows Terminal 配合 WSL2 或直接使用 Node.js。


### 安装 Git for Windows

Pi 在 Windows 上默认使用 Git Bash 执行命令。

启动时会按顺序查找，其中就包括默认路径 C:\Program Files\Git\bin\bash.exe。

如果没有安装 Git for Windows，启动时会找不到 bash，直接安装 Git for Windows 即可解决。

如果不想用 Git Bash，也可以通过 shellPath 配置指定其他 bash，或通过 defaultTools 改用 PowerShell 工具。


### 安装 Node.js

从 nodejs.org 下载安装包，或使用 winget：

```text
# PowerShell
> winget install OpenJS.NodeJS.LTS
```


### 安装 Pi Agent

在 Windows Terminal 的 PowerShell 或 CMD 中执行：

```text
# PowerShell
> npm install -g --ignore-scripts @earendil-works/pi-coding-agent
```


### Windows 特有快捷键

Windows 默认用 Ctrl+Q 发送跟进消息、Alt+Q 取回排队消息，无需重映射。

想改用 Alt+Enter 才需要配置。

在 Windows Terminal 中，Alt+Enter 默认是全屏快捷键。

如果想让 Pi Agent 接收到这个快捷键，需要在 Windows Terminal 设置中移除或重映射全屏快捷键。

在设置中搜索 "toggleFullscreen"，将其快捷键改为其他组合。

然后把 pi 的 app.message.followUp 绑定为 alt+enter。


### 挂起行为

Windows 原生终端不支持 Unix 的作业控制。

原生 Windows 上 Ctrl+Z 被绑定为编辑撤销，挂起需自行绑定一个快捷键。

WSL 下用 Alt+Z 挂起，Ctrl+Z 仍可挂起进程，配合 fg 恢复正常可用。


## Termux（Android）配置

Pi Agent 可以在 Android 设备上通过 Termux 运行。


### 安装步骤

先安装 Termux 本体，请从 F-Droid 获取最新版安装包，再在 Termux 中执行下面的命令。


## 实例

除了 Termux 本体，还需要在手机上安装 Termux:API 应用。

这个应用同样可以从 F-Droid 获取，剪贴板等设备集成能力都依赖它。

只安装 termux-api 命令行包而不装 Termux:API 应用，相关命令不会生效。


### 注意事项

Termux 环境与常规 Linux 有差异，下面几点需要留意。


## tmux 集成

Pi Agent 可以在 tmux 会话中正常工作。


### 优势

把 Pi Agent 放进 tmux，主要为了获得持久化和多窗口能力。


### 推荐配置

在 ~/.tmux.conf 中添加：


## 实例

其中 extended-keys 两行是关键配置，作用是让 Shift+Enter、Ctrl+Enter 等组合键正确传入 pi。

extended-keys-format csi-u 需要 tmux 3.5 或更高版本，可用 tmux -V 查看版本。

```text
$ tmux -V
tmux 3.5a
```

不加这两行，tmux 里 Shift+Enter 会退化成普通回车，多行输入会直接把消息发送出去。

如果 tmux 版本在 3.2 到 3.4 之间，请省略 csi-u 那一行，pi 仍支持 tmux 默认的 xterm 格式。


## 终端设置优化

无论使用哪个终端，下面几项设置都会直接影响 Pi Agent 的显示效果。


### VS Code 集成终端配置

在 VS Code 的 settings.json 中添加以下配置，文件路径为 ~/Library/Application Support/Code/User/settings.json（macOS）：


## 实例


## Shell 别名建议

以下是一套完整的 Pi Agent 别名，各平台通用，可添加到 ~/.zshrc、~/.bashrc 或等效的 shell 配置文件中：


## 实例

如果你使用 fish shell，将 alias 改为 abbr 或使用 fish 的 alias 语法。

```text
# fish shell 使用 abbr 定义缩写
abbr -a pic pi -c
```


## 复习重点

- 能说明 `Pi Agent 多平台部署` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
