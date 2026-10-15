# Claude Code：Coding Plan

- 来源：[Coding Plan](https://www.runoob.com/claude-code/coding-plan.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：学习笔记
- 章节序号：0139

## 本章内容

现在市面上有很多大模型厂商， 国外的有 Anthropic、Open AI、Grok、Gemini等，但是访问国外现在不方便，国内的有 DeepSeek、千问、ZLM、Minimax 等。

我们使用Claude Code 写代码最费钱的就是 token 了，海外的访问不方便，而且还贵，国内的现在都有包月套餐，如果长期用建议买包月套餐划算。

很多厂商都推出了 Coding Plan，它专为 AI 编程工具设计的订阅制服务，整合了千问（Qwen）、GLM、Kimi、MiniMax 等顶级大模型，兼容主流 AI 编程助手（如 Cursor、Claude Code、OpenClaw 等），采用固定月费模式，成本远低于按量计费 API，且彻底杜绝欠费风险。

Coding Plan 核心优势：

- 顶级模型一键接入：无需自己调用百炼 API，直接在熟悉的编程工具里使用最强模型。
- 成本极低：固定月费（Lite ¥40/月，Pro ¥200/月），首月限时优惠仅 7.9 元 / 39.9 元。
- 安全无忧：禁止 API 直连，仅限交互式编程工具使用，避免滥用封禁风险。
- 图片理解支持：qwen3.5-plus、kimi-k2.5 支持上传截图/设计图直接生成代码。

Coding Plan 支持以下工具：Cursor、Claude Code、OpenClaw、OpenCode、Cline（VS Code 扩展）、Kilo Code / Kilo CLI、Qwen Code、Codex 等。


## 订阅方舟 Coding Plan

访问方舟 Coding Plan 活动，按需订阅套餐，用量不大用 Lite 版本就可以了, 如果用量非常大可以使用 Pro 版本。


## Coding Plan/Agent Plan首两个月2.5折

活动时间：2026.06.08-2026.08.07

购买成功后，点击 创建您的 API Key：

然后点创建按钮：

点击下面的小眼睛图标，可以看到 API key 可以，要用时，复制上就可以了：

方舟 Coding Plan 是面向开发者的 AI 编码订阅服务，助力高效开发，核心优势如下：

- 模型丰富：支持主流大语言模型与 Embedding 模型，覆盖 Doubao、DeepSeek、Kimi、GLM、MiniMax 等热门系列。
- 工具兼容广：适配 Claude Code、Cursor、Cline、OpenCode、Codex CLI 等主流 AI 编码工具。
- 额度共享：多工具共用套餐额度，灵活切换，适配不同开发场景。
- 套餐灵活：提供 Lite / Pro 多档方案，满足轻度到高强度开发需求。
- 稳定高可用：多租户隔离与资源调度保障，高峰期依然稳定流畅。

不同的工具配置的 Base URL 根据兼容的协议会有不同：

- 兼容 Anthropic 接口协议工具：https://ark.cn-beijing.volces.com/api/coding
- 兼容 OpenAI 接口协议工具：https://ark.cn-beijing.volces.com/api/coding/v3

注意：请勿使用 https://ark.cn-beijing.volces.com/api/v3 ：该 Base URL 不会消耗您的 Coding Plan 额度，而是会产生额外费用。


### 配置 Claude Code

完成 Claude Code 安装后，还需配置以下信息：

- ANTHROPIC_BASE_URL：https://ark.cn-beijing.volces.com/api/coding
- ANTHROPIC_AUTH_TOKEN：获取您的 API Key
- ANTHROPIC_MODEL：支持两种配置方式 配置具体模型名称（如 kimi-k2.5），可实时切换模型 配置 ark-code-latest，通过控制台切换模型

具体模型有：doubao-seed-2.0-code、doubao-seed-2.0-pro、doubao-seed-2.0-lite、doubao-seed-code、minimax-m2.7、glm-5.1、deepseek-v4-pro、kimi-k2.6。

配置 settings.json

编辑或新建 settings.json 文件，内容如下：

```html
{
  "env": {
    "ANTHROPIC_AUTH_TOKEN": "<ARK_API_KEY>",
    "ANTHROPIC_BASE_URL": "https://ark.cn-beijing.volces.com/api/coding",
    "ANTHROPIC_MODEL": "<Model_Name>"
  }
}
```

请替换以下内容：

- <ARK_API_KEY>：替换为您的 API Key
- <Model_Name>：替换为所需模型名称，例如 kimi-k2.5

settings.json 文件路径：

- MacOS / Linux：~/.claude/settings.json
- Windows：C:\Users\<用户名>\.claude\settings.json

配置 .claude.json：

编辑或新建 .claude.json 文件，添加以下内容：

```text
{
  "hasCompletedOnboarding": true
}
```

.claude.json 文件路径：

- MacOS / Linux：~/.claude.json
- Windows：C:\Users\<用户名>\.claude.json

以下设置 DeepSeek V4 的配置，ANTHROPIC_AUTH_TOKEN 处替换为你自己的 API key：

```html
{
  "env": {
    "ANTHROPIC_BASE_URL": "https://ark.cn-beijing.volces.com/api/coding",
    "ANTHROPIC_AUTH_TOKEN": "<ARK_API_KEY>",
    "API_TIMEOUT_MS": "3000000",
    "ANTHROPIC_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_SONNET_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_OPUS_MODEL": "deepseek-v4-pro[1m]",
    "ANTHROPIC_DEFAULT_HAIKU_MODEL": "deepseek-v4-flash",
    "CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS": "1",
    "ENABLE_TOOL_SEARCH": "true"
  },
  "effortLevel": "max"
}
```

Claude Code + CC Switch 使用 方舟 Coding Plan 配置详情查看：https://www.runoob.com/claude-code/volcengine-coding-plan.html

其他配置文档参考：https://www.volcengine.com/docs/82379/1928262


## 订阅阿里 Coding Plan

Coding Plan 基本太难抢， 也要下架，阿里现在都改为 Token Plan 了，查看：阿里云百炼 Token Plan

- OpenAI 兼容：https://token-plan.cn-beijing.maas.aliyuncs.com/compatible-mode/v1
- Anthropic 兼容：https://token-plan.cn-beijing.maas.aliyuncs.com/apps/anthropic

需要先购买百炼的 Coding Plan 套餐：百炼的 Coding Plan 活动页面

如果用量非常大可以使用 Pro 版本，它是 Lite 版本的 5 倍，支持的模型都一样（现在太火，Lite 版本需要在 9:30 开抢）：

购买完 Coding Plan 套餐，可以在 Coding Plan 页面，获取 Coding Plan 专属 API Key（格式为 sk-sp-xxxxx）。


## 复习重点

- 能说明 `Coding Plan` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
