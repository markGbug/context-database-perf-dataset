# Claude Code：Claude Agent SDK 使用说明

- 来源：[Claude Agent SDK](https://www.runoob.com/claude-code/claude-agent-sdk.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：练习笔记
- 章节序号：0171

## 本章内容

Claude Agent SDK 让你能够构建可以自主读取文件、运行命令、搜索网络、编辑代码等的 AI Agent。

Claude Agent SDK 将驱动 Claude Code 的工具、Agent 循环和上下文管理能力开放为可编程的 Python 和 TypeScript 库。

简单来说，这是一个把 Claude Code 作为库来使用的 SDK，你可以把它嵌入到自己的应用、CI 流水线或自动化脚本中，构建能自主完成复杂任务的 AI Agent。


## 核心能力

SDK 内置了读取文件、运行命令和编辑代码的工具，你的 Agent 无需自己实现工具执行逻辑，可以立即开始工作。主要能力包括：


## 前提条件

- Node.js 18+（TypeScript）或 Python 3.10+
- 一个 Anthropic 账号，并获取 API Key（在此注册）


## 第一步：安装 SDK


### TypeScript

```text
npm install @anthropic-ai/claude-agent-sdk
```

TypeScript SDK 会将适用于你当前平台的 Claude Code 二进制文件作为可选依赖一起打包，无需单独安装 Claude Code。


### Python

```text
# 使用 pip
pip install claude-agent-sdk

# 或使用 uv（推荐）
uv add claude-agent-sdk
```

注意：Claude Code CLI 会自动随包一起安装，无需单独安装！SDK 默认使用打包的 CLI。

如果你希望使用系统级安装或指定版本，可以通过 ClaudeAgentOptions(cli_path="/path/to/claude") 指定路径。


## 第二步：配置 API Key

从 Claude Console 获取 API Key，然后在项目目录创建 .env 文件：

```text
ANTHROPIC_API_KEY=your-api-key-here
```

或直接设置为环境变量：

```text
export ANTHROPIC_API_KEY=your-api-key-here
```


### 支持第三方云平台

SDK 也支持通过第三方 API 提供商进行认证：Amazon Bedrock（设置 CLAUDE_CODE_USE_BEDROCK=1 环境变量并配置 AWS 凭证）、Google Vertex AI（设置 CLAUDE_CODE_USE_VERTEX=1）以及 Microsoft Azure（设置 CLAUDE_CODE_USE_FOUNDRY=1）。

⚠️ 重要：除非事先获得 Anthropic 批准，否则不允许第三方开发者在基于 Claude Agent SDK 构建的产品中提供 claude.ai 登录或速率限制。请使用文档中描述的 API Key 认证方式。


## 第三步：运行你的第一个 Agent

以下示例创建一个 Agent，列出当前目录中的文件：


### Python


## 实例


### TypeScript


## 实例


## 实战：构建一个自动修复 Bug 的 Agent

下面通过一个完整示例，演示 Agent SDK 的核心用法。


### 准备一个有 Bug 的文件

创建 utils.py，包含两处有意为之的 Bug：


## 实例


### 编写 Agent

创建 agent.py：


## 实例


### 运行

```text
python agent.py
```

运行后查看 utils.py，你会看到 Agent 自主完成了以下操作：

- 读取了 utils.py 文件
- 分析了代码逻辑，识别出可能导致崩溃的边界情况
- 编辑了文件，添加了完善的错误处理


## 核心概念解析


### 函数 —— Agent 循环的入口

query 是创建 Agent 循环的主要入口点，返回一个异步迭代器，因此你使用 async for 来实时流式获取 Claude 工作时产生的消息。循环在 Claude 完成任务或遇到错误时结束。SDK 负责编排（工具执行、上下文管理、重试），你只需消费这个消息流。

每次迭代会产生一条消息，可能是：

- Claude 的推理过程
- 一次工具调用
- 工具调用结果
- 最终结果


### 工具（Tools）—— 控制 Agent 能做什么


### 权限模式（Permission Modes）—— 控制人工监督程度


## 自定义 Agent 行为


### 添加 Web 搜索

```text
options = ClaudeAgentOptions(
    allowed_tools=["Read", "Edit", "Glob", "WebSearch"],
    permission_mode="acceptEdits"
)
```


## 后续章节

- 添加自定义系统提示
- 允许执行终端命令
- 加载项目配置（CLAUDE.md 等）
- 错误处理
- Agent SDK vs. 其他 Claude 工具
- SDK 功能对照表

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Claude Agent SDK` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
