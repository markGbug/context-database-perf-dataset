# Hermes Agent：Hermes Agent 技能（Skills）

- 来源：[Hermes Agent Skills](https://www.runoob.com/hermes-agent/hermes-agent-skills.html)
- 分类：AI / 智能开发
- 技术：Hermes Agent
- 笔记类型：练习笔记
- 章节序号：0253

## 本章内容

如果说记忆系统让 Hermes 记住了你是谁，那么技能（Skills）系统让 Hermes 记住了怎么做事。

Skills（技能）是 Hermes Agent 的程序化记忆。

Skills 允许智能体从经验中创建可重用的工作流程，并在未来的会话中复用。

Skills 系统是 Hermes Agent 的核心差异化特性——它是唯一内置学习循环的智能体，能够创建技能、在使用中改进技能，并在会话之间保持知识。


## 技能是什么

Skills 是一组定义智能体行为的指令和工具，它们可以：

- 自动化工作流程 — 封装常见任务模式
- 跨会话学习 — 保存和复用成功的解决方案
- 与社区共享 — 发布和安装他人创建的技能
- 自我改进 — 在使用中不断完善

更多内容参考 Skills 教程：https://www.runoob.com/ai-agent/skills-agent.html。


### 技能 vs 记忆

经验法则：如果你会把它写进参考文档，它就是技能；如果你会把它贴在便利贴上，它就是记忆。


## 技能目录结构

所有技能都存放在 ~/.hermes/skills/ 目录——这是唯一的数据源。

初次安装时，内置技能会从仓库复制到此目录。通过 Hub 安装的技能和 Agent 自动创建的技能也保存在这里。

```text
~/.hermes/skills/
├── mlops/                     # 分类目录
│   ├── axolotl/
│   │   ├── SKILL.md           # 主指令文件（必须）
│   │   ├── references/        # 补充文档（按需加载）
│   │   ├── templates/         # 输出模板
│   │   ├── scripts/           # 辅助脚本
│   │   └── assets/            # 附属资源
│   └── vllm/
│       └── SKILL.md
├── devops/
│   └── deploy-k8s/            # Agent 自动创建的技能
│       ├── SKILL.md
│       └── references/
├── .hub/                      # Skills Hub 状态
│   ├── lock.json
│   ├── quarantine/            # 安全隔离区
│   └── audit.log
└── .bundled_manifest          # 记录内置技能版本
```

每个技能目录的必须文件只有 SKILL.md，其余子目录都是可选的。

Agent 可以修改或删除任何技能——无论是内置的、从 Hub 安装的，还是自己创建的。


## 渐进式披露：Token 高效加载机制

技能系统最聪明的设计之一是渐进式披露——Agent 不会一次性把所有技能内容塞进上下文，而是分三层按需加载。

```text
Level 0: skills_list()              → [{name, description, category}, ...]
                                       会话启动时加载，约 3,000 tokens
                                       ↓ 只有需要用某个技能时，才继续
Level 1: skill_view(name)           → 完整 SKILL.md 内容 + 元数据
                                       ↓ 只有需要参考文档时，才继续
Level 2: skill_view(name, path)     → 技能内的特定 references/ 文件
```

这个设计的实际意义非常直接：

- 你安装了 50 个技能，但本次会话只用了 1 个——只有那 1 个的完整内容会占用 Token
- Level 0 的技能列表（约 3,000 tokens）在每次会话启动时固定加载，让 Agent 知道有哪些技能可以用
- 其余内容在 Agent 判断需要时才加载，不用不花

渐进式披露是技能系统区别于把所有文档塞进系统提示词的关键设计。它保证了技能数量可以无限增长，而每次会话的 Token 成本基本恒定。


## 内置技能一览

Hermes 安装时自带大量内置技能，可以直接使用。

命令行中启动 hermes：

```text
hermes
```

使用 以下命令查看技能相关命令：

```text
/skills
```

以下命令可以在会话中查看所有技能:

```text
/skills browse
```

hermes 直接在命令行中查看:

```text
hermes skills list
```

桌面版直接点击左侧的技能与工具菜单查看：


### 技能分类

内置技能按功能分类存放在子目录中：


### 可选技能（不默认安装）

可选技能随 hermes-agent 一起发布，存放在 optional-skills/ 下，但默认不激活，需要显式安装。

这类技能通常需要额外依赖或是小众用途：


## 实例


## 使用技能

技能有两种触发方式：斜杠命令直接调用和自然语言自动触发。


### 斜杠命令直接调用

每个已安装的技能都自动成为一个斜杠命令。

在任何平台（CLI、Telegram、Discord 等）中直接使用：


## 实例

内置的 plan 技能是个好例子：运行 /plan [请求] 后，技能指令会告诉 Hermes 先检查上下文，再生成 Markdown 格式的实现计划并保存到 .hermes/plans/，而不是直接执行任务。


### 自然语言触发

也可以通过自然对话触发技能，Hermes 会通过 skill_view 工具自动加载：


## 实例

Agent 会识别出需要 arxiv 技能，自动加载后执行。


### 关键字搜索技能


## 实例


## 从 Hub 安装技能

除了内置技能，你还可以从 agentskills.io 社区 Hub 安装第三方技能。


### 命令行安装


## 实例

安装后发生了什么：

- 技能目录被复制到 ~/.hermes/skills/
- 出现在 skills_list 输出中
- 可以作为斜杠命令使用

已安装的技能在新会话中生效。如果想在当前会话立即使用，用 /reset 开启新会话，或加 --now 参数立即刷新提示缓存（会多消耗一些 Token）。


### 验证安装


## 实例


### 从 GitHub 仓库添加技能源


## 实例


## /learn 命令：一键从源生成技能

/learn 是将你已知的东西——或一堆参考资料——快速转化为可复用技能的捷径，无需手写 SKILL.md。

它是开放式的：指向任何你能描述的内容，Agent 用它已有的工具收集材料，然后按照标准创作规范生成技能。


## 实例


## 后续章节

- /learn 的工作原理
- Agent 自动创建技能
- 触发时机
- 手动要求 Agent 创建技能
- 实例
- 控制技能写入权限
- 实例
- SKILL.md 格式详解
- 实例
- 字段限制
- 条件激活：智能显隐机制
- 实例
- 技能包（Skill Bundle）：组合加载
- 创建技能包
- 实例
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Hermes Agent Skills` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
