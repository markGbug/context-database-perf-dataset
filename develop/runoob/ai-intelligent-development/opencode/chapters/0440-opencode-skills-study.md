# OpenCode：OpenCode Skills

- 来源：[OpenCode Skills](https://www.runoob.com/opencode/opencode-skills.html)
- 分类：AI / 智能开发
- 技术：OpenCode
- 笔记类型：学习笔记
- 章节序号：0440

## 本章内容

在 OpenCode 中，代理技能（Skills）是一种用于封装可复用行为的机制，通过 SKILL.md 文件定义，使 LLM 能够按需加载、按需执行特定能力。

相比普通提示词，技能更接近模块化能力单元，可以在多个项目或团队中复用。

Skills 是 OpenCode 的能力插件系统，它将 AI 行为从单次提示升级为可复用能力模块，使开发流程更加标准化、可组合，并适用于复杂工程体系。

Skills 以 Markdown 文件形式存在，不执行功能，而是通过按需、渐进式加载，实现高效且可复用的经验传递。

Skills 和传统 Prompt 最大的区别是：按需加载 + 渐进式披露（只在需要时才把厚厚的 SOP 塞进上下文，极大节省 token）。


### 核心机制

Skills 通过内置的 skill 工具进行管理，工作流程如下：

- 扫描本地和全局技能目录
- 在上下文中暴露可用技能列表
- 代理根据任务自动选择技能
- 按需加载 SKILL.md 内容

这种机制避免了将所有规则一次性加载，提高了性能和上下文利用率。


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

如果你需要一些参考资料，参考实例，执行脚本，可以使用更复制 Skill 的目录结构：

```text
my-skill/
├── SKILL.md      # 必需：指令 + 元数据
├── scripts/      # 可选：可执行代码
├── references/   # 可选：文档资料
└── assets/       # 可选：模板、资源
```


### 技能如何工作

技能用渐进式加载来高效管理上下文：

- 发现：启动时，AI 只加载每个技能的名称和描述，只保留最基本的识别信息。
- 激活：当任务匹配某个技能的描述时，AI 才把完整的 SKILL.md 指令读入上下文。
- 执行：AI 按照指令执行，按需加载参考文件或运行代码。

这种设计让 AI 保持快速，同时能按需获取更多信息。


## 文件放置位置

每个技能需要一个独立的文件夹，文件夹内放置 SKILL.md 文件（注意：文件名必须全部大写）。OpenCode 会自动搜索以下六个位置：

典型的项目目录结构如下：

```text
your-repo/
├── .opencode/
│   └── skills/
│       ├── git-release/
│       │   └── SKILL.md      ← 发版流程技能
│       ├── code-review/
│       │   └── SKILL.md      ← 代码审查技能
│       └── api-doc/
│           └── SKILL.md      ← API 文档编写技能
├── src/
└── package.json
```


## 发现机制

OpenCode 的技能发现分为两个层级：

- 项目本地技能：OpenCode 从当前工作目录开始，向上逐层遍历目录树，直到到达 Git 工作树的根目录为止。在此过程中，它会收集沿途每一层目录下 .opencode/skills/*/SKILL.md、.claude/skills/*/SKILL.md、.agents/skills/*/SKILL.md 中所有匹配的技能文件。
- 全局技能：同时从 ~/.config/opencode/skills/*/SKILL.md、~/.claude/skills/*/SKILL.md、~/.agents/skills/*/SKILL.md 中加载所有已定义的全局技能。

两个层级的技能会合并后一起提供给代理使用。如果项目本地技能与全局技能同名，项目本地技能优先。


## 编写 SKILL.md


### 1、Frontmatter 字段

每个 SKILL.md 文件必须以 YAML frontmatter 开头（即 --- 包裹的部分）。OpenCode 只识别以下字段，未知字段会被自动忽略：


### 2、命名规则

name 字段的值必须同时满足以下所有条件，否则技能将无法被加载：

- 长度为 1–64 个字符
- 只能包含小写字母和数字，单词之间可以用单个连字符（-）分隔
- 不能以 - 开头或结尾
- 不能包含连续的 --
- 必须与包含该 SKILL.md 的文件夹名称完全一致

等效的正则表达式：

```text
^[a-z0-9]+(-[a-z0-9]+)*$
```

合法命名示例：git-release、api-doc、code-review、deploy2prod

非法命名示例：Git-Release（含大写）、-release（以 - 开头）、git--release（连续 --）


### 3、编写描述

description 字段的内容直接影响代理是否能正确选择和调用该技能。建议描述要具体明确，说明该技能做什么、在什么场景下使用，避免过于笼统：

- ❌ 过于笼统：帮助完成发版任务
- ✅ 具体明确：从合并的 PR 中起草发版说明、提出版本号建议，并生成可直接使用的 gh release create 命令


### 4、完整示例

在项目中创建 .opencode/skills/git-release/SKILL.md，内容如下：


## 实例

Frontmatter 中的 name 值必须与文件夹名称一致。本例中文件夹名为 git-release，因此 name 也必须写 git-release，否则技能无法被识别。


## 代理如何发现和加载技能

OpenCode 启动后，会将当前所有可用技能以 XML 格式注入到 skill 工具的描述中。代理可以通过查看工具描述来了解有哪些技能可用：

```html
<available_skills>
  <skill>
    <name>git-release</name>
    <description>Create consistent releases and changelogs</description>
  </skill>
  <skill>
    <name>code-review</name>
    <description>Perform structured code reviews with consistent criteria</description>
  </skill>
</available_skills>
```

当代理判断某个技能与当前任务相关时，会主动调用 skill 工具来加载该技能的完整 SKILL.md 内容：

```text
skill({ name: "git-release" })
```

加载完成后，技能中定义的指令和上下文信息会进入代理的工作记忆，从而影响后续的行为和输出。技能本身不会自动执行任何操作，只是为代理提供额外的上下文和行为规范。


## 配置技能权限

在 opencode.json 中，使用 permission.skill 字段控制代理可以访问哪些技能，支持精确名称和 Glob 通配符两种匹配方式：


## 实例

三种权限动作对技能的具体效果如下：


## 按代理覆盖权限

不同代理可能需要访问不同的技能集，可以为每个代理单独配置权限，覆盖全局默认值。


### 1、在自定义代理的 Frontmatter 中配置

```text
# 文件路径：~/.config/opencode/agents/my-agent.md
---
permission:
  skill:
    "documents-*": "allow"    # 该代理可以加载所有 documents- 开头的技能
                               # 其他技能遵循全局权限配置
---

You are a documentation assistant.
```


### 2、在 opencode.json 中为内置代理配置

```text
{
  "$schema": "https://opencode.ai/config.json",
  "agent": {
    "plan": {                          // 内置代理名称
      "permission": {
        "skill": {
          "internal-*": "allow"        // plan 代理可以加载 internal- 开头的技能，
                                       // 即使全局配置中对其设置了 deny
        }
      }
    }
  }
}
```


## 禁用技能工具

对于完全不需要使用技能的代理，可以直接禁用 skill 工具。禁用后，<available_skills> 列表将从代理的上下文中完全移除，既节省 Token 消耗，又避免代理尝试加载任何技能。


### 1、在自定义代理的 Frontmatter 中禁用


## 实例


### 2、在 opencode.json 中为内置代理禁用


## 实例


## 排查技能加载问题

如果某个技能没有出现在可用列表中，请按以下顺序逐项检查：

- 确认文件名大小写 SKILL.md 的文件名必须全部大写，写成 skill.md 或 Skill.md 都不会被识别。
- 检查 Frontmatter 完整性 确保 SKILL.md 开头有正确的 YAML frontmatter，且包含 name 和 description 两个必填字段。缺少任意一个，技能都不会被加载。
- 确认技能名称唯一且格式正确 如果不同路径下存在同名技能，可能产生冲突。同时检查 name 字段是否符合命名规则（仅小写字母和数字，以连字符分隔），且与文件夹名称完全一致。
- 检查权限配置 在 opencode.json 的 permission.skill 中，权限为 "deny" 的技能会对代理完全隐藏，不会出现在 <available_skills> 列表中。检查是否有通配符规则（如 "*": "deny"）意外匹配到了该技能。

更多 Skills 可以参考：

- Skills 教程：https://www.runoob.com/ai-agent/skills-agent.html


## 复习重点

- 能说明 `OpenCode Skills` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
