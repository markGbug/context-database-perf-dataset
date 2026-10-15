# Claude Code：Claude Code API 配置

- 来源：[Claude Code API 配置](https://www.runoob.com/claude-code/claude-code-setup.html)
- 分类：AI / 智能开发
- 技术：Claude Code
- 笔记类型：概念卡
- 章节序号：0137

## 本章内容

Claude 在国内用，API 其实不是很友好，除了 Claude 官方的模型，我能用其他 AI 模型吗？

本章节会详细教你如何配置多个国内主流 AI 模型的 API，让 Claude Code 支持：

进入对应控制台后，注册/登录 → 完成实名认证 → 创建 API Key 即可开始调用。


### API 管理工具

平台一多，配置起来就麻烦，我们可以使用第三方工具 CC Switch 可以帮我们轻松管理这几个热门工具的 API 配置：https://github.com/farion1231/cc-switch/，Windows / macOS / Linux 全支持。

CC Switch 是一个 Claude Code / Codex / Gemini CLI 的全方位辅助工具。

CC Switch 可以帮我们轻松管理这几个热门工具的 API 配置，就好比给你的开发工具箱来了个智能整理助手，所有工具的配置都能在它这有序管理。

各平台安装包下载地址：https://github.com/farion1231/cc-switch/releases。

具体的操作设置参考文章：https://www.runoob.com/ai-agent/cc-switch.html

如果你不闲麻烦，可以参照下文，自行配置。


## DeepSeek 接入 Claude Code

需要的信息：

- API key： https://platform.deepseek.com/api_keys 申请 API keys。
- BASE_URL：API 请求的 URL 为 https://api.deepseek.com/anthropic。


### 环境变量中配置

Linux / Mac 用户执行以下命令配置 DeepSeek Anthropic API 环境变量，其中 API Key 在 DeepSeek Platform 获取：

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

Windows 用户执行：

```text
$env:ANTHROPIC_BASE_URL="https://api.deepseek.com/anthropic"
$env:ANTHROPIC_AUTH_TOKEN="<你的 DeepSeek API Key>"
$env:ANTHROPIC_MODEL="deepseek-v4-pro[1m]"
$env:ANTHROPIC_DEFAULT_OPUS_MODEL="deepseek-v4-pro[1m]"
$env:ANTHROPIC_DEFAULT_SONNET_MODEL="deepseek-v4-pro[1m]"
$env:ANTHROPIC_DEFAULT_HAIKU_MODEL="deepseek-v4-flash"
$env:CLAUDE_CODE_SUBAGENT_MODEL="deepseek-v4-flash"
$env:CLAUDE_CODE_EFFORT_LEVEL="max"
```

注意：模型配置要加 [1m] , 然后记得思考强度要开启 max，才能让它用满血状态去跑。

参数说明：

精简为前三列（参数名 / 示例值 / 作用说明）如下：

然后进入项目目录，执行 claude 命令，即可开始使用了。

```text
cd my-project
claude
```

启动 Claude Code 后，指定使用 DeepSeek：

```text
claude --model deepseek-v4-pro
```

或在交互模式中切换：

```text
> /model deepseek-v4-pro
```

输入 /model 可以查看支持的模型：

参考文档：https://api-docs.deepseek.com/zh-cn/guides/coding_agents


## 阿里百炼接入 Claude Code


## 记忆卡片

- 一句话定义：`Claude Code API 配置` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
