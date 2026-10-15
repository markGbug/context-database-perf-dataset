# Skills（技能）：SKILL.md 文件

- 来源：[SKILL.md 文件](https://www.runoob.com/skills/skill-md-file.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：学习笔记
- 章节序号：0624

## 本章内容

SKILL.md 是 Agent Skills 的核心文件。

本节将深入讲解 SKILL.md 的完整结构和所有可用字段。


## 基本结构

一个 SKILL.md 文件包含两个主要部分：

- YAML Frontmatter（元数据区域）
- Markdown 内容（指令区域）


## 完整示例


## 元数据字段详解

以下是 SKILL.md 支持的所有元数据字段：


## name 字段详解

name 字段是技能的标识符，必须遵循以下规则：

- 长度：1-64 个字符
- 字符限制：只能使用 Unicode 小写字母（a-z）和连字符（-）
- 开头结尾：不能以连字符开头或结尾
- 连续字符：不能包含连续连字符（--）
- 匹配要求：必须与父目录名称一致

有效示例:

```text
name: pdf-processing
name: data-analysis
name: code-review
```

无效示例:

```text
name: PDF-Processing   # 错误：不能使用大写字母
name: -pdf           # 错误：不能以连字符开头
name: pdf--processing  # 错误：不能包含连续连字符
```


## description 字段详解

description 字段是最重要的字段之一，它告诉代理什么时候应该激活这个技能。

一个好的描述应该：

- 描述技能的功能（做什么）
- 说明使用场景（什么时候用）
- 包含关键词，帮助代理识别相关任务

好的描述示例:

```text
description: 从 PDF 文件中提取文本和表格，填写 PDF 表单，合并多个 PDF。处理 PDF 文档或用户提及 PDF、表单或文档提取时使用。
```

不好的描述示例:

```text
description: 帮助处理 PDF 文件。  # 太笼统，代理无法判断何时使用
```

提示：description 字段会在对话开始时被加载。请确保它包含足够的关键词，以便代理能够正确识别何时需要激活该技能。


## license 字段详解

license 字段用于指定技能的许可证。这是可选字段。

```text
license: Apache-2.0
# 或者引用 bundled 的许可证文件
license: Proprietary. LICENSE.txt has complete terms
```


## compatibility 字段详解

compatibility 字段用于说明技能的环境要求。只有当技能有特殊的环境要求时才需要添加。

```text
# 指定目标产品
compatibility: Designed for Claude Code

# 指定系统依赖
compatibility: Requires git, docker, jq, and access to the internet

# 指定编程语言版本
compatibility: Requires Python 3.14+ and uv
```

注意：大多数技能不需要 compatibility 字段。只有当技能确实有特定的环境要求时才添加。


## metadata 字段详解

metadata 字段可以存储任意的键值对信息。客户端可以使用它来存储规范中未定义的额外属性。

```text
metadata:
  author: example-org
  version: "1.0"
  tags:
    - pdf
    - document
    - extraction
```

提示：建议使用相对独特的键名，以避免与其他技能发生冲突。


## allowed-tools 字段详解

allowed-tools 是一个实验性字段，用于指定技能可以使用的预批准工具。

```text
allowed-tools: Bash(git:*) Bash(jq:*) Read
```

注意：这是一个实验性功能，不同的代理实现可能支持程度不同。


## 指令区域详解

元数据区域之后的 Markdown 内容是技能的指令部分。这里没有格式限制，你可以根据需要编写任何内容。

建议包含以下内容：

- 分步操作说明
- 输入输出示例
- 常见边界情况处理

```text
# 技能名称

## 功能说明

简要描述这个技能做什么。

## 操作步骤

1. 第一步：执行某个操作
2. 第二步：执行另一个操作
3. 第三步：完成最终操作

## 示例

### 输入示例
描述输入是什么...

### 输出示例
描述输出是什么...

## 注意事项

- 注意点 1
- 注意点 2
```

注意：一旦技能被激活，整个 SKILL.md 文件会被加载到上下文中。建议将主要指令保持在 500 行以内、5000 tokens 以下。将详细的参考材料移到单独的文件中。


## 复习重点

- 能说明 `SKILL.md 文件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
