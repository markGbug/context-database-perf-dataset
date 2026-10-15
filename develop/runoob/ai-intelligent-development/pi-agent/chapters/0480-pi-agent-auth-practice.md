# Pi Agent：Pi Agent 认证与模型配置

- 来源：[Pi Agent 认证与模型配置](https://www.runoob.com/pi-agent/pi-agent-auth.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：练习笔记
- 章节序号：0480

## 本章内容

Pi Agent 支持两种认证方式：订阅登录和 API Key。本章详细介绍如何配置，让 Pi Agent 连接到 AI 模型。


## 认证方式概览


## 方式一：订阅登录（推荐）

如果你已经订阅了 Claude Pro/Max、ChatGPT Plus/Pro 或 GitHub Copilot，这是最便捷的方式。

启动 Pi Agent 后，输入以下命令：

```text
/login
```

然后在出现的菜单中选择你的订阅提供商：

Claude Pro/Max 订阅认证模式下，Pi Agent 使用的是额外用量（extra usage），按 token 计费，不占用你的 Claude 计划额度。你可以在 Claude 用量设置 中查看。

完成登录后，凭证会存储在 ~/.pi/agent/auth.json 中，之后启动 Pi Agent 会自动使用。

如需退出登录，使用：

```text
/logout
```


## 方式二：API Key 环境变量

如果你有 API Key，可以在启动 Pi Agent 前设置环境变量：

```text
# 设置 Anthropic API Key
export ANTHROPIC_API_KEY=sk-ant-api03-your-key-here

# 启动 Pi Agent
pi
```

Pi Agent 支持以下主要提供商的 API Key 环境变量：


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

如果你不想每次手动设置环境变量，可以将 export 命令写入 shell 配置文件（如 ~/.zshrc 或 ~/.bashrc），使其永久生效。


## 方式三：API Key 凭证文件

你也可以通过 /login 命令，选择 API Key 提供商来存储凭证。

存储位置为 ~/.pi/agent/auth.json，格式如下：

```text
{
  "anthropic": { "type": "api_key", "key": "sk-ant-api03-your-key" },
  "openai": { "type": "api_key", "key": "sk-your-openai-key" },
  "deepseek": { "type": "api_key", "key": "sk-your-deepseek-key" }
}
```

凭证文件会自动设置为 0600 权限（仅用户可读写），安全性有基本保障。


## 凭证解析顺序

当 Pi Agent 需要获取 API Key 时，按以下优先级查找：

- CLI 参数 --api-key（最高优先级）
- auth.json 文件中的凭证
- 环境变量
- models.json 中自定义提供商的 Key

也就是说，如果你同时设置了环境变量和 auth.json，auth.json 中的值会优先生效。


## auth.json 高级功能

auth.json 不仅支持存储明文 Key，还支持以下高级用法：


### 从命令行获取 Key

使用 ! 前缀执行命令来获取 Key，适合从密码管理器读取：

```text
{
  "anthropic": {
    "type": "api_key",
    "key": "!security find-generic-password -ws 'anthropic-api-key'"
  },
  "openai": {
    "type": "api_key",
    "key": "!op read 'op://vault/item/credential'"
  }
}
```

上例展示了从 macOS Keychain 和 1Password CLI 获取 Key 的方式。


### 环境变量插值

使用 $ 前缀引用环境变量：

```text
{
  "anthropic": {
    "type": "api_key",
    "key": "$MY_ANTHROPIC_KEY"
  }
}
```


## 切换模型

配置好认证后，你可以随时切换使用的 AI 模型：

交互模式中使用 /model 命令或按 Ctrl+L 打开模型选择器。

使用 Ctrl+P / Shift+Ctrl+P 在已配置的模型间循环切换。

命令行方式指定模型：

```text
# 指定提供商和模型
$ pi --provider anthropic --model claude-sonnet-4-20250514

# 使用 provider/model 格式
$ pi --model openai/gpt-4o "帮我重构这段代码"

# 指定推理等级（thinking level）
$ pi --model sonnet:high "解决这个复杂问题"
```

推理等级（Thinking Level）控制模型在回答前进行多深度的思考。等级从 off（关闭）到 max（最大），推理越深回答质量可能越高，但消耗的 token 也越多。

编辑器的边框颜色会随推理等级变化，让你直观地看到当前推理深度。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pi Agent 认证与模型配置` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
