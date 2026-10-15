# OpenCode：OpenCode 配置文件

- 来源：[OpenCode 配置文件](https://www.runoob.com/opencode/opencode-setup-file.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：练习笔记
- 章节序号：0422

## 本章内容

OpenCode 使用 JSON 格式来配置。

我们可以先看在全局配置文件 ~/.config/opencode/opencode.json：

```text
touch ~/.config/opencode/opencode.json
```

包含模型提供商及配置信息：

```text
{
  // JSON Schema（用于编辑器校验和自动补全）
  "$schema": "https://opencode.ai/config.json",

  "provider": {
    // 自定义 Provider 名称（使用时：deepseek/xxx）
    "deepseek": {

      // 使用 OpenAI 兼容适配器（适用于 DeepSeek 这类兼容接口）
      "npm": "@ai-sdk/openai-compatible",

      "options": {
        // API 基础地址（必须是 OpenAI 兼容格式）
        "baseURL": "https://api.deepseek.com/v1",

        // API Key
        "apiKey": "sk-xxxx",

        // 是否强制设置缓存 key（提升缓存命中率，降低成本）
        "setCacheKey": true
      },

      "models": {
        // 本地模型别名（CLI/TUI 中使用：deepseek/Deepseek-v4）
        "Deepseek-v4": {
          // 实际调用的模型名称（API 层）
          "name": "deepseek-v4-pro"
        }
      }
    }
  }
}
```


### 一个最小可用配置示例

```text
{
  "$schema": "https://opencode.ai/config.json",
  "model": "anthropic/claude-sonnet-4-5",
  "autoupdate": true,
  "theme": "default"
}
```

常用全局配置项：

Provider 示例:

```text
{
  "provider": {
    "anthropic": {
      "options": {
        "timeout": 600000,
        "setCacheKey": true
      }
    }
  }
}
```


## 理解配置的"合并机制"

OpenCode 的配置不是覆盖，而是分层合并。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenCode 配置文件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
