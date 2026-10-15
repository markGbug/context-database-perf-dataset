# OpenCode：OpenCode oh-my-openagent 使用教程

- 来源：[OpenCode oh-my-openagent](https://www.runoob.com/opencode/opencode-oh-my-openagent.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：概念卡
- 章节序号：0443

## 本章内容

Oh My OpenAgent（简称 OmO）是一个开源的 AI 编程助手增强插件，前身叫 oh-my-opencode。

oh-my-openagent 运行在 OpenCode这个 AI 编程工具之上，把它变成一个由 11 个专业 AI Agent 组成的开发团队。

用一句话解释：

你发一个需求 → OmO 自动调度多个 AI 并行工作 → 比单个 AI 快数倍

目前在 GitHub 上有 54k+ Stars，是最受欢迎的 OpenCode 插件。

- Github 地址：https://github.com/code-yeongyu/oh-my-openagent
- 官网：https://ohmyopenagent.com/zh


### 安装

将以下提示词复制粘贴到你的大模型工具（ OpenCode、Claude Code、AmpCode、Cursor 等）：

```text
按照此链接说明安装并配置 oh-my-opencode：https://raw.githubusercontent.com/code-yeongyu/oh-my-openagent/refs/heads/dev/docs/guide/installation.md
```

执行后，它就会自己安装好，安装过程可能有 API key 的配置选项，可以选择配置，也可以不配置：


## 认识 11 位 AI 团队成员（Agent）

OmO 内置了 11 个专门的 Agent，各司其职：


### 核心 Agent


### 专业 Agent


### 工具型 Agent（快速、低成本）

💡 新手提示：你不需要手动选择 Agent。Sisyphus 会根据你的任务类型自动调度合适的 Agent 组合。


## 三种工作模式


### 模式一：ultrawork（最轻松）

在提示词里加 ultrawork 或 ulw，一切自动化：

```text
ultrawork 帮我把这个 React 组件改成 TypeScript
```

适合：日常开发任务，希望 AI 全自动完成的场景。


### 模式二：Prometheus 计划模式（最精准）

按 Tab 键 进入 Prometheus 模式。AI 会先通过问答了解你的需求，生成详细执行计划，确认后再开始执行。

流程：

- 按 Tab 切换到 Prometheus 模式
- 描述你的需求，AI 会问你一些澄清问题
- AI 生成执行计划，你确认
- 输入 /start-work 开始执行

适合：复杂功能开发、架构重构等需要精确规划的场景。


### 模式三：普通对话（最灵活）

直接输入你的问题或需求，不加任何关键词：

```text
解释一下 src/auth.ts 里的 JWT 验证逻辑
```

适合：问问题、代码解释、小修改等轻量任务。


## 配置文件详解

OmO 有两个配置文件，优先级不同：

- 项目级配置（优先级更高）：.opencode/oh-my-opencode.jsonc
- 用户级配置（全局默认）：~/.config/opencode/oh-my-opencode.jsonc

配置文件支持注释（JSONC 格式），也支持 JSON Schema 自动补全：

```text
{
  "$schema": "https://raw.githubusercontent.com/code-yeongyu/oh-my-openagent/dev/assets/oh-my-opencode.schema.json",

  "agents": {
    // 主协调 Agent，建议用 Claude Opus 系列或 Kimi
    "sisyphus": {
      "model": "anthropic/claude-opus-4-6"
    },
    // 架构顾问，建议用 GPT 系列
    "oracle": {
      "model": "openai/gpt-5.4",
      "variant": "high"
    }
  }
}
```

新手建议：安装完成后先不要修改配置，默认设置已经很好。


## 常用命令速查表

在对话界面内：


## 常见问题排查


### Q：安装后运行 opencode 没有看到 OmO 的功能

解决：检查配置文件是否正确注册了插件：

```text
cat ~/.config/opencode/opencode.json
```

确认 plugin 字段包含 "oh-my-opencode"。如果没有，重新运行 bunx oh-my-opencode install。


### Q：运行时提示 "Using legacy package name" 警告

解决：把 opencode.json 中的插件名从 "oh-my-opencode" 更新为 "oh-my-openagent"：

```text
{
  "plugin": ["oh-my-openagent"]
}
```


### Q：Sisyphus Agent 效果很差，感觉和普通 Claude 差不多

原因：可能没有使用 Claude Opus 模型，或没有在提示词中加 ultrawork。

解决：

- 确认已登录 Claude Pro/Max 账号
- 在提示词中加入 ultrawork 关键词
- 运行 bunx oh-my-opencode doctor 检查模型配置


### Q：任务执行到一半停了

解决：继续提示 ultrawork 继续之前的任务，Sisyphus 会通过 Todo 系统恢复进度。


### Q：想禁用匿名遥测数据

OmO 默认启用了匿名遥测（使用 PostHog，数据经过哈希处理）。如需关闭：

```text
export OMO_SEND_ANONYMOUS_TELEMETRY=0
# 或
export OMO_DISABLE_POSTHOG=1
```


## 记忆卡片

- 一句话定义：`OpenCode oh-my-openagent` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
