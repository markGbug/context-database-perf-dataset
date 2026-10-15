# AI Agent（智能体）：Pi Coding Agent 入门教程

- 来源：[Pi Coding Agent](https://www.runoob.com/ai-agent/pi-coding-agent.html)
- 分类：AI / 智能开发
- 技术：AI Agent（智能体）
- 笔记类型：学习笔记
- 章节序号：0033

## 本章内容

Pi 是一个运行在终端里的 AI 编码 Agent，类似于 Claude Code、OpenAI Codex CLI 这类工具。

Pi 的官方理念是："There are many agent harnesses but this one is yours"（Agent 工具很多，但这个是你自己的）。

你给 Pi 一句话，它就能在你的项目目录里读文件、写文件、跑命令，循环调用大模型直到完成任务。

核心理念是用最小的内核加极强的可扩展性，让你把工具改造成适合自己的样子，而不是反过来去适应工具。

Pi Agent 完整教程：https://www.runoob.com/pi-agent/pi-agent-tutorial.html


### Pi 包含什么

Pi 不是一个单独的程序，而是一套由四个 npm 包组成的工具链。

普通用户只需安装最上层的 @earendil-works/pi-coding-agent，就能得到一个开箱即用的命令行 Agent。


### 适合谁用

Pi 特别适合以下场景和人群：

- 偏好终端工作流、不想在 IDE 和命令行之间来回切换的开发者
- 想要一个可以深度定制、甚至让 Agent 自己改写自己的工具的进阶用户
- 需要同时接入多家大模型（Anthropic、OpenAI、Google 等）的人
- 想把 Agent 能力嵌入到自己程序里的开发者（通过 SDK 或 RPC 模式）

注意：Pi 默认以你的用户权限运行，没有内置沙箱。在不受信任的代码仓库上使用前，请先阅读本文的「安全须知」章节。


## 核心设计哲学：原语而非功能

理解 Pi 的设计哲学，你会明白它为什么故意「不内置」很多其他 Agent 都有的功能。

Pi 把这个理念叫做 Primitives, Not Features（提供原语，而非功能）。


### 故意不内置的功能

下面这些功能，Pi 都没有内置，而是让你按需通过扩展或外部工具来实现：


### 为什么要这样做

Pi 认为这些功能在不同团队里需求差异巨大，强行内置反而会让工具变得臃肿且难以贴合实际工作流。

所以它的做法是：保留一个干净的最小内核，把所有「功能」都变成可安装、可编写、可分享的扩展、技能、提示模板和主题。

甚至你可以直接让 Pi 帮你把这些功能写出来，写完用 /reload 重载，立刻就能用。

这句话值得记住：Adapt Pi to your workflows, not the other way around（让 Pi 适应你的工作流，而不是你适应 Pi）。


## 架构与核心包

Pi 由四个层级分明的包组成，上层依赖下层。

你平时用的 pi 命令，只是最上层那个包提供的入口。


### 四个核心包


### 四种运行模式

Pi 不只能交互式运行，它提供了四种模式来适配不同场景：


## 安装

Pi 提供多种安装方式，覆盖 macOS、Linux 和 Windows。

最常见的是用 npm 全局安装，也可以用官方的一键脚本。


### 方式一：一键脚本（推荐新手）

macOS 和 Linux 用户用 curl：

```text
curl -fsSL https://pi.dev/install.sh | sh
```

Windows 用户用 PowerShell：

```text
powershell -c "irm https://pi.dev/install.ps1 | iex"
```


### 方式二：npm 全局安装

如果你已经装了 Node.js，用包管理器全局安装即可。

注意那个 --ignore-scripts 参数：它会跳过依赖的安装期生命周期脚本，Pi 正常使用不需要这些脚本，加上更安全。

```text
# npm 安装
npm install -g --ignore-scripts @earendil-works/pi-coding-agent

# pnpm 安装
pnpm add -g --ignore-scripts @earendil-works/pi-coding-agent

# bun 安装
bun add -g --ignore-scripts @earendil-works/pi-coding-agent
```


### 验证安装

安装完成后，查看版本号确认是否成功：

```text
pi --version
```

例如：

```text
$ pi --version
0.80.6
```


### 卸载

卸载方式取决于你当初用什么装的：

```text
# curl 装的或 npm 装的
npm uninstall -g @earendil-works/pi-coding-agent

# pnpm 装的
pnpm remove -g @earendil-works/pi-coding-agent

# bun 装的
bun uninstall -g @earendil-works/pi-coding-agent
```

注意：卸载 Pi 不会删除你的配置。设置、凭证、会话记录、已安装的 Pi 包都保留在 ~/.pi/agent/ 目录里，需要手动清理。


## 配置模型 Provider

Pi 本身不包含大模型，它需要你提供至少一个模型供应商（Provider）的访问凭证。

配置方式有两种：订阅登录，或 API Key。


### 方式一：订阅登录（最省事）

如果你已经有 Claude Pro/Max、ChatGPT Plus/Pro 或 GitHub Copilot 订阅，可以直接登录复用。

启动 Pi 后运行 /login，然后选择供应商即可：

```text
# 启动 pi
pi

# 在 pi 里执行登录命令
/login
```

可选的订阅供应商有三种：

登录后凭证会存进 ~/.pi/agent/auth.json，过期会自动刷新。退出登录用 /logout。


### 方式二：API Key（最灵活）

用环境变量传入 API Key 是最通用的方式。比如用 Anthropic 的 Key：

```text
# 设置环境变量后启动
export ANTHROPIC_API_KEY=sk-ant-...
pi
```

你也可以在 Pi 里运行 /login 并选择 API Key 类型的供应商，把 Key 持久化存进 auth.json。


### 常见供应商的环境变量

Pi 支持 15 家以上的供应商，下面列出最常见的几家：

提示：auth.json 里的凭证优先级高于环境变量。如果两处都配了，以 auth.json 为准。


### auth.json 的结构

如果你想手动管理凭证，可以直接编辑 ~/.pi/agent/auth.json。这个文件创建时会被设为 0600 权限（仅当前用户可读写）：

```text
{
  "anthropic": { "type": "api_key", "key": "sk-ant-..." },
  "openai": { "type": "api_key", "key": "sk-..." },
  "google": { "type": "api_key", "key": "..." }
}
```

Key 字段还支持三种高级写法，方便从密码管理器或环境变量里取值：


### 云平台供应商

如果你用的是云上的模型服务，Pi 也支持 Azure OpenAI、Amazon Bedrock、Google Vertex AI、Cloudflare 等。

这些通常需要额外配置端点、区域或部署名。以 Azure OpenAI 为例：

```text
# Azure OpenAI 所需的环境变量
export AZURE_OPENAI_API_KEY=...
export AZURE_OPENAI_BASE_URL=https://your-resource.ai.azure.com

# 可选：API 版本与部署名映射
export AZURE_OPENAI_API_VERSION=2024-02-01
export AZURE_OPENAI_DEPLOYMENT_NAME_MAP=gpt-4o=my-gpt4o
```


### 配置 DeepSeek 供应商

Pi 通过 models.json 支持自定义供应商，配置文件地址：

- Linux / macOS：~/.pi/agent/models.json
- Windows：%USERPROFILE%\.pi\agent\models.json

先在 DeepSeek 开放平台获取 API Key：https://platform.deepseek.com/api_keys。

```text
{
  "providers": {
    "deepseek": {
      "baseUrl": "https://api.deepseek.com",
      "api": "openai-completions",
      "apiKey": "$DEEPSEEK_API_KEY",
      "models": [
        {
          "id": "deepseek-v4-pro",
          "name": "DeepSeek V4 Pro",
          "contextWindow": 1000000,
          "maxTokens": 384000,
          "input": ["text"],
          "reasoning": true,
          "cost": {
            "input": 1.74,
            "output": 3.48,
            "cacheRead": 0.145,
            "cacheWrite": 0
          },
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek",
            "reasoningEffortMap": {
              "minimal": "high",
              "low": "high",
              "medium": "high",
              "high": "high",
              "xhigh": "max"
            }
          }
        },
        {
          "id": "deepseek-v4-flash",
          "name": "DeepSeek V4 Flash",
          "contextWindow": 1000000,
          "maxTokens": 384000,
          "input": ["text"],
          "reasoning": true,
          "cost": {
            "input": 0.14,
            "output": 0.28,
            "cacheRead": 0.028,
            "cacheWrite": 0
          },
          "compat": {
            "requiresReasoningContentOnAssistantMessages": true,
            "thinkingFormat": "deepseek",
            "reasoningEffortMap": {
              "minimal": "high",
              "low": "high",
              "medium": "high",
              "high": "high",
              "xhigh": "max"
            }
          }
        }
      ]
    }
  }
}
```

设置环境变量：

Linux / Mac 用户：

```text
export DEEPSEEK_API_KEY="<你的 DeepSeek API Key>"
```

Windows 用户：

```text
$env:DEEPSEEK_API_KEY="<你的 DeepSeek API Key>"
```

进入项目目录并执行 pi 命令：

```text
cd /path/to/my-project
pi
```

输入 /model 打开模型切换器，选择 deepseek，然后选择 DeepSeek-V4-Pro 或 DeepSeek-V4-Flash。

更多配置选项请参阅：https://github.com/earendil-works/pi/blob/main/packages/coding-agent/docs/models.md。


### 凭证解析顺序

当 Pi 需要某个供应商的凭证时，按以下顺序依次查找，找到即用：


## 第一次运行

配置好凭证后，进入你的项目目录，直接运行 pi 启动。

```text
# 进入项目目录
cd /path/to/project

# 启动 pi
pi
```

启动后，直接输入一句话并回车，比如让它分析这个仓库：

```text
Summarize this repository and tell me how to run its checks.
```

Pi 会自动读取文件、运行命令，然后给出总结和检查方式。


### 项目信任提示

如果当前目录或上层目录里有 .pi 配置、扩展、技能等项目级资源，Pi 在交互式启动时会先问你信不信任这个项目。

这是为了防止一个仓库在你不知情时静默加载它的扩展或修改设置。

注意：信任决策保存在 ~/.pi/agent/trust.json。非交互模式（-p、--mode json）不会弹窗，默认按全局设置里的 defaultProjectTrust 处理。


### Agent 是怎么工作的

你每发一条消息，Pi 就会启动一个 agent 循环。理解这个循环，就理解了 Pi 的工作方式。

核心是中间那个 turn 循环：模型每轮可能调用工具，Pi 执行工具把结果塞回上下文，再让模型继续，直到模型不再调用工具、给出最终回复。


## 后续章节

- 四个内置工具
- 控制可用工具
- 用 AGENTS.md 给项目下指令
- 写一个 AGENTS.md
- Pi 从哪里加载指令
- 修改系统提示
- 交互模式常用操作
- 引用文件：@
- 运行 shell 命令：!
- 切换模型与思考强度
- 输入与编辑技巧
- 边跑边插话
- 常用斜杠命令速查
- 会话管理：树形历史
- 会话存在哪里
- 在会话树里导航

## 复习重点

- 能说明 `Pi Coding Agent` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
