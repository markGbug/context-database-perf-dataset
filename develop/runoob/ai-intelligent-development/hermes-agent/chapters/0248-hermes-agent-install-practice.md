# Hermes Agent：Hermes Agent 安装

- 来源：[Hermes Agent 安装](https://www.runoob.com/hermes-agent/hermes-agent-install.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：练习笔记
- 章节序号：0248

## 本章内容

Hermes Agent 支持以下操作系统：

系统配置：

Windows 用户必须使用 WSL2（Windows Subsystem for Linux），Hermes Agent 目前不原生支持 Windows 命令行。


## 安装方式选择


### 方式一：Hermes Desktop（macOS / Windows 推荐）

Hermes Desktop 是官方出品的桌面应用，在命令行工具之上提供了图形化界面——包含可视化 Dashboard、Profile 管理器、技能浏览器等，安装桌面应用时会同时安装命令行工具（hermes 命令），两者可以并用。

- 访问官网 hermes-agent.nousresearch.com
- 点击 Download For... 按钮
- 运行下载的安装程序，按提示完成安装。

下载后双击安装即可：

安装完成后，hermes 命令会自动添加到系统路径，可以在终端直接使用。

整个面板如下所示：


### 方式二：命令行安装（Linux / macOS / WSL2）

打开终端，执行以下命令即可自动完成安装:

```text
curl -fsSL https://get.hermes-agent.nousresearch.com | bash
```

```text
iex (irm https://hermes-agent.nousresearch.com/install.ps1)
```

脚本会自动检测系统环境并安装所有依赖。

以上命令会自动完成以下所有步骤：

- 检测缺失的依赖并安装（uv、Python 3.11、Node.js v22、ripgrep、ffmpeg）
- 克隆 Hermes Agent 仓库到 ~/.hermes/hermes-agent/
- 创建隔离的 Python 虚拟环境
- 配置全局 hermes 命令
- 引导你完成 LLM 提供商配置

Windows 系统说明：不支持原生 Windows 环境，请先安装 WSL2，再在 WSL2 终端中执行上述命令。

如果安装过 OpenClaw 还可以直接导入配置：

这里选择不导入，输入 n，进入模型设置，选择第一个快速设置：

接下来我们选择倒数第二项的 More providers：

这里可以选择更多国内或国际的大模型：

接下来我们使用 字节方舟 Coding Plan ，所以选择的是 Customer endpoint，就是自定义 API 地址与 API key。

Base URL 设置字节方舟兼容 OpenAI 接口协议工具：https://ark.cn-beijing.volces.com/api/coding/v3

设置 API key 与支持的大模型，比如 ark-code-latest。

安装完成后，刷新 Shell:

```text
source ~/.bashrc   # Bash 用户
# 或
source ~/.zshrc    # Zsh 用户
```

```text
hermes --version
```

使用以下命令开启智能体对话：

```text
hermes
```


### 文件安装位置说明：

参考文档：hermes-agent.nousresearch.com/docs/getting-started


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Hermes Agent 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
