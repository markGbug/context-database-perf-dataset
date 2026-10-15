# DeepSeek Harness：DeepSeek Harness 教程

- 来源：[DeepSeek Harness 教程](https://www.runoob.com/deepseek-harness/deepseek-harness-tutorial.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：概念卡
- 章节序号：0215

## 本章内容

DeepSeek Harness 是由深度求索（DeepSeek AI）开发、于 2026 年 8 月正式开源的 Agent Harness（智能体框架），采用 MIT 许可证，代码以 TypeScript 编写。

DeepSeek Harness 采用一切皆插件的开放架构：模型、工具、技能、会话、沙箱、存储、循环、调度、UI 等所有 Agent 能力均由插件组合而成，可以自由替换和灵活重组——无需改动源码，即可在配置层定制你自己的 Agent。

DeepSeek AI 官方理念：Agent = Model + Harness。官方标语：Everything is a Plugin.（一切皆插件）


## 谁适合阅读本教程？

本教程面向以下几类读者：

- 开发者 / 工程师：想要一个能力边界完全可控、每个组件都可以替换重组的本地 AI 编码助手——而不是被厂商锁定在固定功能里的黑盒。
- AI / ML 从业者：对 Agent 架构感兴趣——底层由 Cordis 插件系统驱动，事件驱动设计有论文支撑，PTC 模式还能让模型用 TypeScript 程序组合多步工具调用。
- 效率工具爱好者：希望用 Web UI 图形界面、headless 命令行或 Python SDK 把 Agent 嵌入自己的工作流。
- 研究人员：需要可观测的 Agent——每一次运行都写入仅追加会话日志，可在 Trajectory 视图中查看系统提示词、思维链、工具调用与子 Agent 调度。
- 注重开源可控的用户：MIT 开源协议，配置层自由组合，无遥测、无云端锁定，完全自主掌控。


## 阅读前需要具备的基础能力

本教程不要求 AI 研究背景或深度机器学习知识。你需要具备：

操作系统要求：Linux、macOS 或 Windows（安装 Node.js 后即可运行）。


## 核心特性

DeepSeek Harness 特性：

- 🧩 一切皆插件 — Cordis 内核只负责插件的加载、卸载与依赖管理；模型、工具、技能、会话、沙箱、存储、循环、调度、UI 等所有能力均由插件提供，并通过服务与事件彼此协作，配置层自由组合
- 📜 运行有迹可循 — 模型看到的一切（系统提示词、思维链、工具调用与结果、子 Agent 调度、上下文注入）都写入仅追加设计的会话日志；Trajectory 视图按来源查看，恢复、分叉、检索与回放共享同一份事件流
- 🛠️ 四种运行模式 — 标准模式（功能完整的编码 Agent）、PTC 模式（模型用一段 TypeScript 程序组合多轮工具调用）、极简模式（双工具，用于模型基准测试）、创造模式（运行时检查 + 插件试验 + 自定义 preset 创作）
- 🌐 多形态使用 — Web UI（默认 http://127.0.0.1:3080）、headless（一次性运行、打印最终答案并退出）、CLI、Python SDK、TypeScript SDK
- 🔌 工具与扩展丰富 — 文件编辑、Shell、文件与网页检索、Skills、计划、目标、子代理、工作流；事件驱动扩展点（会话 / Agent / 能力三级事件），任何能力都可被 patch 替换
- 🔒 开放可控 — MIT 开源；Profile + 组合包分层叠加配置，dsh --profile web --dump-config 可查看实际启动的完整配置树；无特权内核，所有注册皆可逆
- 🤖 模型无关 — 填入 DeepSeek API 密钥即可用，支持其他提供方与自定义 OpenAI 兼容端点，模型路由无需重启
- 🔬 研究就绪 — 完整可观测的事件流与配置树，面向 Agent 架构研究的开放设计（底层 Cordis 有学术论文支撑）


## 相关资源

官方资源


## 记忆卡片

- 一句话定义：`DeepSeek Harness 教程` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
