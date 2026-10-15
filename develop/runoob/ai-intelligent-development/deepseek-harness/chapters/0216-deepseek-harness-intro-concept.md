# DeepSeek Harness：DeepSeek Harness 简介

- 来源：[DeepSeek Harness 简介](https://www.runoob.com/deepseek-harness/deepseek-harness-intro.html)
- 分类：AI / 智能开发
- 技术：DeepSeek Harness
- 笔记类型：概念卡
- 章节序号：0216

## 本章内容

AI 模型已经能独立完成复杂的编码任务，真正的挑战不再是让模型更聪明，而是怎么把它的能力稳定、可靠、可观测地组织成一个真正可用的 Agent。

2026 年 8 月，深度求索开源了 DeepSeek Harness（dsh）——一个一切皆插件的 Agent 框架，给出了这个问题的答案：Agent = Model + Harness。模型是 Agent 的灵魂，而 Harness 给予 Agent 理解环境、使用工具、在真实场景中持续工作的能力。


## 什么是 DeepSeek Harness？

DeepSeek Harness（dsh）是深度求索（DeepSeek AI）开发的开源 Agent Harness（智能体框架），采用 MIT 许可证，以 TypeScript 编写，于 2026 年 8 月正式开源，目前处于开发者预览阶段（官方提示未来将有破坏兼容性的变更）。

DeepSeek Harness 不优化模型本身，而是优化模型运行的环境，一切皆插件（Everything is a Plugin）。

模型、工具、技能、会话、沙箱、存储、循环（agent loop）、调度、UI 等所有 Agent 能力均由插件提供，通过 Cordis 内核的服务（Service）与事件（Event）彼此协作——开发者无需改动任何源码，就能在配置层选择、替换、扩展任一能力。

底层由开源插件系统 Cordis 驱动，其设计思想对应论文《A Programming Paradigm for Spatiotemporal Composability》。运行时不存在需要打补丁的特权内核：每一项能力注册都是可逆副作用，插件卸载时自动撤销，因此扩展 dsh 的方式就是把新插件挂载到其他插件旁边。

"Everything is a Plugin."（一切皆插件）—— DeepSeek Harness 官方标语

模型是 Agent 的灵魂，Harness 给予 Agent 理解环境、使用工具，并在真实场景中持续工作的能力。—— DeepSeek Harness 官网


## 为什么需要 Harness？

行业的结论已经越来越一致：瓶颈不在模型智能，而在基础设施。OpenAI 团队在 100 万行代码实验中，5 个月产出全部由 Agent 完成、工程师一行代码未写。

LangChain 仅优化外部驾驭环境（文档结构、验证回路、追踪系统），就让编码 Agent 在 Terminal Bench 2.0 的得分从 52.8% 飙升至 66.5%，全球排名从第 30 位跃升至第 5 位——底层模型一个参数都没动。

DeepSeek Harness 正是这一共识的产品化落地：不追求更强的模型，而是把模型运行所需的约束、反馈、工具、记忆、可观测性全部做成可组合的插件基础设施，让每个团队都能按自己的方式驾驭 AI。


## AI 工程范式的三次跃迁

要理解 Harness 为何重要，需要先看清楚我们是怎么一步步走到这里的：

DeepSeek Harness 是驾驭工程理念的完整产品化：一个把约束、反馈、可观测、可替换全部落地的开源实现，让驾驭工程不再停留在方法论，而是开箱即用的基础设施。


## 核心架构：一切皆插件

DeepSeek Harness 的架构可以用一张图说清：Cordis 内核居中，所有能力以插件环绕，通过服务与事件协作。

这套架构落实到运行时的关键机制是 Profile + 组合包（Bundle）：运行中的 dsh 是一棵插件树，由启动时按序叠加的各层组合而成——先按 profile 列出的顺序应用每个组合包，然后是 profile 的 cordis.patch.yml、home 级 patch，最后是任意 --patch overlay。用一行命令即可查看机器上实际启动的完整配置树：


## 四种运行模式

DeepSeek Harness 开箱即提供四种运行模式，覆盖从完整编码 Agent 到最小化基准测试的全谱系：


## 核心特性


### 特性一：每一次运行都有迹可循

模型看到的一切都会写入仅追加（append-only）设计的会话日志：系统提示词、思维链、工具调用与结果、子 Agent 调度、每一次上下文注入，全部落盘。在 Trajectory 视图中可按来源查看；恢复、分叉（fork）、检索与回放共享同一份事件流——Agent 的每一步都可追溯、可复现。


### 特性二：多形态使用，随处运行

Web UI（默认 http://127.0.0.1:3080）提供完整的图形界面；headless 模式一次性运行任务、打印最终答案并退出，适合脚本与 CI；还有 CLI 与官方 Python SDK（pip install deepseek-harness-sdk，自带运行时、无需系统 Node.js）和 TypeScript SDK，把 Agent 嵌入任何工作流。


### 特性三：开放可控，无特权内核

MIT 开源，不存在需要打补丁的特权内核：所有能力注册都是可逆副作用，插件卸载即撤销。通过 Profile、组合包与 patch 分层叠加配置，--dump-config 可随时审查整棵配置树——你的 Agent 是什么样，你说了算。


### 特性四：模型无关，即插即用

填入 DeepSeek API 密钥即可使用，也支持其他提供方与自定义 OpenAI 兼容端点，模型路由无需重启服务器。事件驱动的扩展点体系（会话 / Agent / 能力三级事件）让开发者可以挂载策略与适配器，随时换模型、换工具、换存储。


## 快速上手

安装 Node.js 后，一行命令启动 Web UI：

```text
npx @deepseek-ai/dsh web
```

也可以从源码安装：

```text
git clone https://github.com/deepseek-ai/deepseek-harness.git
cd deepseek-harness
pnpm install
pnpm run build
pnpm dsh web
```

Web UI 使用只需三步：


## Harness 与相关工具的关系

DeepSeek Harness 不是又一个"写几个 agent 的库"，而是位于 SDK 与框架之上、解决"Agent 如何可靠运行"的完整层。与当下热门工具的定位差异：


## 记忆卡片

- 一句话定义：`DeepSeek Harness 简介` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
