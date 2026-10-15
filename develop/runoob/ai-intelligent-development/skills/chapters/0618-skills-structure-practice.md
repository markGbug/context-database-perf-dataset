# Skills（技能）：Skills 基本结构

- 来源：[Skills 基本结构](https://www.runoob.com/skills/skills-structure.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：练习笔记
- 章节序号：0618

## 本章内容

Skills 的核心本质，是给 AI 制定标准化执行流程的操作指引，规则一经编写完成，就能像程序函数一样，被反复调用、直接复用。

Skills 以 Markdown 文本载体存储，本身不直接执行功能。

Skills 按需加载、渐进式调用的特性，高效沉淀工作经验，实现能力快速复用与精准传递。


## Skill 的核心结构

Skills 的核心就是：一个文件夹 + 一个 SKILL.md 文件。

SKILL.md 文件包含：

- 元数据（至少要有名称和描述）
- 告诉 AI 如何完成某一特定任务的指令

一个 Skill 本质上就是一个 Markdown 文件（文件名固定为 SKILL.md）

```text
my-skill/
└── SKILL.md   （唯一必需）
```

SKILL.md 基本模板:

```text
---
name: your-skill-name
description: 一句话描述该 Skill 的功能和使用场景
---

# Skill 名称

## 使用指引
[给 AI 的分步骤行为指引]

## 示例
[该 Skill 的具体使用示例]
```

整个 SKILL.md 分为上下两部分：用 --- 包裹的 YAML frontmatter（头部配置），以及下方的 Markdown 正文（执行说明）。

接下来我们逐一拆解每个部分:


### Frontmatter：两个必填字段

Frontmatter 是 SKILL.md 顶部用 --- 包裹的 YAML 配置块，是整个 Skill 的身份信息。

官方只规定两个必填字段：

字段一：name（技能名称）

name 字段最多 64 个字符，只能包含小写字母、数字和连字符。

```text
name: processing-pdfs        # 好：动名词形式，清晰描述功能
name: analyzing-spreadsheets # 好：一眼知道用途
name: my-brand-guidelines    # 好：组织专属知识

name: helper      # 差：太模糊
name: MySkill     # 差：包含大写字母（不合规）
name: data files  # 差：包含空格（不合规）
```

推荐使用动名词形式（动词 + -ing）来命名，如 processing-pdfs、analyzing-spreadsheets，这样能清晰描述 Skill 提供的活动或能力。

字段二：description（触发条件描述）

这是最重要的字段。启动时，系统只会把所有 Skills 的 name 和 description 预加载进系统提示词。

只有当 description 被 AI 判断与当前任务相关时，才会进一步读取完整的 SKILL.md 内容。

description 应该同时包含两部分：这个 Skill 做什么，以及什么时候 Claude 应该使用它。

```text
description: |
  Use when the user needs to create, read, edit, or generate Word
  documents (.docx). Triggers include: 'Word doc', 'word document',
  '.docx', 'report', 'letter', 'memo', or any request to produce
  a formatted document for sharing or printing.
```


### Markdown 正文：执行说明的内部结构

Frontmatter 之后是 Markdown 正文，告诉 AI 具体怎么做。

至少包含两个区块：


### SKILL.md 实例

SKILL.md 基本模板:

```text
---
name: pdf-processing
description: 从 PDF 中提取文本和表格，填写表单，并合并文档
---

# PDF 处理

## 使用场景
当需要对 PDF 文件进行操作时使用，例如：

- 提取 PDF 文本或表格数据
- 填写 PDF 表单
- 合并多个 PDF 文件

## 提取文本
- 使用 `pdfplumber` 提取文本型 PDF 内容
- 扫描版 PDF 需配合 OCR 工具

## 填写表单
- 读取 PDF 表单字段
- 按输入数据填充并生成新文件
```

最小必填示例:

```text
---
name: skill-name
description: 说明该 Skill 的功能以及适用场景
---
```

含可选字段示例:

```text
---
name: pdf-processing
description: 从 PDF 中提取文本和表格，填写表单，并合并文档
license: Apache-2.0
metadata:
  author: example-org
  version: "1.0"
---
```

字段说明：


## Skill 的文件目录结构

一个技能就是一个文件夹，至少包含一个 SKILL.md 文件，根据需要，还可以包含其他目录和文件。

为避免上下文膨胀：

- 核心规则 → SKILL.md
- 详细资料 → 单独文件
- 实用逻辑 → 脚本执行（不加载）

推荐结构:

```text
my-skill/
├── SKILL.md          # 必需：元数据 + 指令
├── scripts/          # 可选：可执行代码
      └── helper.py
├── references/       # 可选：参考文档
├── assets/           # 可选：模板、资源
└── ...               # 其他文件或目录
```

各目录的作用如下：

- SKILL.md：必需文件，包含技能的元数据和执行指令
- scripts/：可选目录，包含代理可以执行的可执行代码
- references/：可选目录，包含详细的参考资料
- assets/：可选目录，包含静态资源如模板、图片等


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Skills 基本结构` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
