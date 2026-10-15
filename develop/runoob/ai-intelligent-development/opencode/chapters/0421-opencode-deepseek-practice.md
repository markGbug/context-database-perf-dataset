# OpenCode：OpenCode 接入 DeepSeek

- 来源：[OpenCode DeepSeek](https://www.runoob.com/opencode/opencode-deepseek.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：练习笔记
- 章节序号：0421

## 本章内容

OpenCode 是一款开源的 AI 编程助手，支持在终端、网页等多种环境中运行。

本章节我们要配置 DeepSeek 作为其 AI 后端，从而在编程中获得强大的智能辅助。


### OpenCode 下载与安装

首先，请根据你的操作系统访问 OpenCode 官方下载页面 https://opencode.ai/zh/download，获取安装包或安装脚本：

为了避免因版本差异导致的兼容性问题，我们强烈建议将 OpenCode 升级到最新版本，并确保版本号 ≥ v1.14.24。

最简单的安装与升级就是一键命令安装：

```text
curl -fsSL https://opencode.ai/install | bash
```

安装完成后，可以在终端中运行以下命令来验证版本：

```text
opencode --version
```

如果版本显示低于 v1.14.24，请重新下载最新版本进行覆盖安装。


## 运行与配置 DeepSeek

OpenCode 启动后，可以通过内置的命令行交互来快速接入 DeepSeek。

需要的基本信息：

- API key： https://platform.deepseek.com/api_keys 申请 API keys。
- BASE_URL：API 请求的 URL 为 https://api.deepseek.com/anthropic。


### 1、启动 OpenCode

进入项目目录（如：cd runoob-opencode-test），在终端中直接运行：

```text
opencode
```

此时会进入 OpenCode 的交互界面。


### 2、启用连接配置模式

在 OpenCode 的输入框中输入以下命令并回车：

```text
/connect
```

系统会进入连接配置流程，提示你选择 AI 模型供应商。


### 3、选择供应商为 DeepSeek

当出现供应商列表后，输入 deepseek 并确认选择。


### 4、填入 DeepSeek API Key

接下来，你需要输入 DeepSeek 的 API Key。可以从 DeepSeek 开放平台 申请并获取你的专属 Key。

请输入 DeepSeek API Key：sk-xxxxxxxxxxxxxxxxxxxxxxxx

建议提前将 API Key 保存到安全的位置，并注意不要泄露。


### 5、选择模型

在支持的模型列表中，选择 DeepSeek-V4-Pro，即可完成配置。

最大思考强度设置 max:

配置完成后，所有通过 OpenCode 发起的 AI 请求都将使用你指定的 DeepSeek-V4-Pro 模型来生成响应。你可以立即在编程场景中体验 DeepSeek 带来的高效与智能。

至此，我们已经成功将 DeepSeek 接入 OpenCode。


## 实例测试

进入项目目录

```text
cd runoob-opencode-test
```

启动 OpenCode：

```text
opencode
```

输入提示词：

```text
生成一个企业级的专业 [游戏宣传] 落地页。
添加交互元素与动画效果，并确保页面具备完全响应式设计。
请给我带来惊喜，充分发挥创意，按步骤完成此项任务。
```

查看效果，还是非常不错的：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCode DeepSeek` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
