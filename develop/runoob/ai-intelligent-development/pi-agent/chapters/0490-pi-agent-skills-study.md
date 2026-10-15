# Pi Agent：Pi Agent Skills 技能系统

- 来源：[Pi Agent Skills 技能系统](https://www.runoob.com/pi-agent/pi-agent-skills.html)
- 分类：AI / 智能开发
- 技术：Pi Agent
- 笔记类型：学习笔记
- 章节序号：0490

## 本章内容

Skills（技能）是自包含的能力包，让 AI 可以按需加载专业领域的工作流指令和工具脚本。

Pi Agent 实现了 Agent Skills 标准。


## 什么是 Skill

一个 Skill 就是一个包含 SKILL.md 文件的目录。

SKILL.md 中包含技能的名称、描述和详细的使用指令，AI 会在需要时自动读取并执行。

你可以把 Skill 理解为 AI 的「专业培训手册」——平时不占上下文空间，需要时才加载。


## Skill 工作原理

整个加载过程分四步，核心思路是"先看目录，再读全文"。

- Pi Agent 启动时扫描所有 Skill 位置，提取名称和描述
- 所有可用 Skill 的描述以 XML 格式嵌入系统提示词中
- 当用户的任务匹配某个 Skill 的描述时，AI 会自动用 read 工具加载完整的 SKILL.md
- AI 按照 SKILL.md 中的指令工作，使用相对路径引用技能目录中的脚本和资源

需要注意，模型不一定主动读取，必要时在提示词中明确要求，或用 /skill:名称 强制加载。

这种设计被称为「渐进式披露（Progressive Disclosure）」——只有描述始终在上下文中，完整的指令按需加载。


## Skill 的目录结构

只有 SKILL.md 是必需的，其余目录按需创建。

```text
my-skill/
├── SKILL.md              # 必需：Frontmatter + 指令
├── scripts/              # 辅助脚本
│   └── process.sh
├── references/           # 详细参考文档（按需加载）
│   └── api-reference.md
└── assets/
    └── template.json
```


## SKILL.md 格式

SKILL.md 使用 YAML Frontmatter 定义元信息，之后是 Markdown 格式的指令正文：


## 实例

引用技能目录中的文件时，使用相对路径。


## Frontmatter 字段

只有 name 和 description 必填，其余字段按需添加。

description 是 AI 决定是否加载你的 Skill 的关键依据，务必写得具体明确。

一个模糊的 description 会导致 Skill 在不合适的场景被触发，或者在需要的场景被忽略。


## Skill 加载位置

Pi Agent 会在全局和项目两个层级扫描 Skill，不同位置的发现规则略有差异。

补充一点：在 ~/.agents/skills/ 与项目 .agents/skills/ 中，分组子目录里声明了合法 Frontmatter 的嵌套 .md 文件也会被识别，而顶层没有 Frontmatter 的 .md 会被忽略。

CLI 参数 --no-skills 可禁用技能自动发现，但显式给出的 --skill 路径 仍会加载。


## 校验与命名冲突

Pi Agent 会按 Agent Skills 标准校验 Skill，多数问题只给出警告，Skill 仍会加载。

缺少 description 的 SKILL.md 不会被加载，畸形文件同样只给警告且不加载。

同名 Skill 来自不同位置时会发出警告，并保留最先发现的那个。


## Skill 命令

每个 Skill 自动注册为 /skill:名称 命令：

```text
/skill:brave-search
/skill:pdf-tools extract
```

命令后的参数会以 User: 参数 的形式追加到 Skill 内容中。

以 /skill:pdf-tools extract report.pdf 为例，展开后的内容大致如下：

```text
/skill:pdf-tools extract report.pdf

User: extract report.pdf
```

AI 收到这份内容后，会按 SKILL.md 中的指令去查找并执行 scripts/ 目录下的脚本。

可以通过设置禁用 Skill 命令注册：


## 实例

也可以通过设置中的 disable-model-invocation 让某些 Skill 仅能手动调用，不自动出现在系统提示词中。


## 从其他工具导入 Skill

Pi Agent 可以加载 Claude Code 或 OpenAI Codex 的 Skills：

下面两个配置分别写入全局与项目的 settings.json，路径按你的实际目录调整。


## 实例

对于项目级的 Claude Code Skills：


## 实例

Skills 中的指令可以要求 AI 执行任意操作，包括运行可执行文件。

在使用第三方 Skill 之前，建议先审查其内容。


## 完整 Skill 示例

以下是一个网页搜索 Skill 的完整示例：


## 实例


## Skill 仓库推荐

这两个仓库提供了大量可直接使用的 Skill，安装前仍建议通读一遍内容。


## 复习重点

- 能说明 `Pi Agent Skills 技能系统` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
