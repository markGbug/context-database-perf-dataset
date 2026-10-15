# Vibe Coding：Claude Code 入门教程

- 来源：[Claude Code 入门教程](https://www.runoob.com/vibe-coding/claude-code.html)
- 分类：AI / 智能开发
- 技术：Vibe Coding
- 笔记类型：概念卡
- 章节序号：0687

## 本章内容

Claude Code 是 Anthropic 官方 CLI 级智能体工具。

Claude Code 定位不是聊天，而是 在本地代码仓库中执行高权限、可上下文感知的工程任务。

Claude Code 是 Agent，不是 Chat。

详细教程参见：https://www.runoob.com/claude-code/claude-code-tutorial.html

核心能力：

- 直接读取整个项目目录
- 理解真实代码结构
- 执行多文件修改
- 严格遵循指令而非对话取悦


### 安装配置

MacOS/Linux:

```text
curl -fsSL https://claude.ai/install.sh | bash
```

Homebrew (MacOS):

```text
brew install --cask claude-code
```

Windows:

```text
irm https://claude.ai/install.ps1 | iex
```

NPM:

使用 npm 安装 请确保你的系统的安装了 Node.js，版本需在 v18 或更高。

```text
npm install -g @anthropic-ai/claude-code
```

接下来就可以开始进入你创建的项目目录，开始使用 Claude Code：

```text
cd your-project
claude
```


### 登录您的账户

使用 claude 命令启动交互式会话时，您需要登录：

```text
claude
# 首次使用时会提示您登录
/login
# 按照提示使用您的账户登录
```

如果你可以正常使用 Anthropic 的账号，就可以开始使用，如果没有国内可以使用 DeepSeek 或 GLM 等。


## DeepSeek 接入 Claude Code

安装 Claude Code 后，我们在终端中设置以下环境变量：

```text
export ANTHROPIC_BASE_URL=https://api.deepseek.com/anthropic
export ANTHROPIC_AUTH_TOKEN=<你的 DeepSeek API Key>
export ANTHROPIC_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_OPUS_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_SONNET_MODEL=deepseek-v4-pro[1m]
export ANTHROPIC_DEFAULT_HAIKU_MODEL=deepseek-v4-flash
export CLAUDE_CODE_SUBAGENT_MODEL=deepseek-v4-flash
export CLAUDE_CODE_EFFORT_LEVEL=max
```

参数说明：

- CLAUDE_CODE_EFFORT_LEVEL：思考深度，可选 low / medium / max
- ANTHROPIC_MODEL：指定使用 deepseek-v4-pro[1m] 模型
- CLAUDE_CODE_DISABLE_NONESSENTIAL_TRAFFIC=1：禁用非必要流量

然后进入项目目录，执行 claude 命令，即可开始使用了。

```text
cd my-project
claude
```

参考文档：https://api-docs.deepseek.com/zh-cn/guides/anthropic_api


## 阿里百炼接入 Claude Code


## 记忆卡片

- 一句话定义：`Claude Code 入门教程` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
