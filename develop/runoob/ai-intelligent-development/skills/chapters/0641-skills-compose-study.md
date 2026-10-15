# Skills（技能）：Skills 组合与编排

- 来源：[Skills 组合与编排](https://www.runoob.com/skills/skills-compose.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：学习笔记
- 章节序号：0641

## 本章内容

单个 Skill 解决单一问题，而复杂的工作流往往需要多个 Skill 协同配合。

本篇介绍如何设计 Skill 之间的依赖关系，以及在 SKILL.md 中编排多 Skill 工作流。


## 组合模式：两种思路

Claude 在单次对话中可以跨 Skill 调用，但一次只能"主动读取"一个 Skill 的正文。复杂的多 Skill 工作流，通常由一个"编排 Skill"来统筹调度。


## 顺序编排示例

以"上传 PDF → 提取文字 → 生成 Word 摘要报告"为例，三个 Skill 依次协作。

```html
---
name: pdf-to-word-report
description: >
  将 PDF 文档转换为 Word 格式的摘要报告，包含文字提取、
  内容分析和格式化输出三个阶段。当用户需要从 PDF 生成报告、
  提取 PDF 内容并整理为 Word 文档时触发。
---

# PDF 转 Word 摘要报告

## 工作流程

本 Skill 协调三个处理阶段，最终生成 .docx 报告。

### 阶段一：提取 PDF 文字
使用 pdf-reading Skill（位于 /mnt/skills/public/pdf-reading/）的处理逻辑：

```bash
python /mnt/skills/public/pdf-reading/scripts/extract.py \
  --input  <PDF路径> \
  --output /home/claude/extracted_text.txt
```

完成后告知用户：已提取 {N} 页内容，共 {字数} 字。

### 阶段二：生成摘要内容
对提取的文字进行内容分析，生成：
- 文档主题（1句话）
- 关键章节摘要（每章 2-3 句）
- 重要数据与结论

将摘要内容写入 /home/claude/summary.json

### 阶段三：生成 Word 报告
使用 docx Skill 的规范，调用：

```bash
python /mnt/skills/public/docx/scripts/generate.py \
  --template /mnt/skills/public/docx/assets/report_template.docx \
  --data     /home/claude/summary.json \
  --output   /mnt/user-data/outputs/report.docx
```

完成后调用 present_files 展示下载链接。
```


## 通过脚本实现 Skill 组合

当多个 Skill 共享脚本时，可以通过主脚本直接调用其他 Skill 的脚本，形成处理管道。


## 实例


## 避免循环依赖

当 Skill A 依赖 Skill B、Skill B 又依赖 Skill A 时，会形成循环依赖，导致无法执行。

设计 Skill 组合时，应保持单向依赖关系。


## 共享工具函数

多个 Skill 都需要的通用函数，可以提取为公共模块，避免重复实现。


## 实例


## 复习重点

- 能说明 `Skills 组合与编排` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
