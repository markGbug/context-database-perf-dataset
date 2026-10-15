# Pi Agent：Pi Agent 支持的 AI 提供商

- 来源：[Pi Agent 支持的 AI 提供商](https://www.runoob.com/pi-agent/pi-agent-appendix-providers.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：概念卡
- 章节序号：0502

## 本章内容

以下是 Pi Agent 支持的所有 AI 提供商的完整列表。


## 支持订阅登录的提供商

通过 /login 命令进行 OAuth 登录：

订阅类入口以 Pi Agent /login 菜单实际显示为准，不同版本可能略有差异。


## 支持 API Key 的提供商

通过环境变量或 ~/.pi/agent/auth.json 配置 API Key：

```text
$ export ANTHROPIC_API_KEY=sk-ant-api03-xxxx
```

API Key 提供商共 35 个，与官方 providers.md 的环境变量清单一一对应。

其中 Qwen Token Plan（Individual）与 Qwen Token Plan 共用同一个环境变量 QWEN_TOKEN_PLAN_API_KEY，区别在于 auth.json 键名以及可选模型范围。

Cloudflare 两项的账号与网关 ID 既可以作为环境变量设置，也可以写进 auth.json 凭证的 env 对象。


## 本地与自定义提供商

本地推理后端通过配置文件接入，自定义接口则可以用扩展方式注册。

扩展方式注册提供商的完整示例见《与 llama.cpp 本地模型》一章。

以下三个本地后端都通过 OpenAI Compatible API 接入：

把以下最小示例写入 ~/.pi/agent/models.json，以 Ollama 为例，LM Studio 与 vLLM 只需替换名称和 baseUrl：


## 实例

示例中的 apiKey 取值 ollama 只是占位符，本地服务端会直接忽略它。

但不能因此把它删掉：没有配置任何鉴权字段时模型会正常加载，却不会出现在 /model 选择器里，官方也建议保留占位值。

除 apiKey 外的各字段含义如下：


## 记忆卡片

- 一句话定义：`Pi Agent 支持的 AI 提供商` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
