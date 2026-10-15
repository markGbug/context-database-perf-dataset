# 知识点 51100：Skills（技能）：多 Skill 协作工作流 - 编排 Skill 的 SKILL.md

- 来源：[多 Skill 协作工作流](https://www.runoob.com/skills/skills-project-multi.html)
- 来源章节：[0652-skills-project-multi-study.md](../chapters/0652-skills-project-multi-study.md)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 所在小节：编排 Skill 的 SKILL.md
- 知识类型：代码
- 原章节序号：0652

## 原文片段

```text
---
name: report-pipeline
version: 1.0.0
description: >
  完整的数据报告生成流水线：自动对上传的 CSV/Excel 文件执行数据清洗、
  统计分析并生成 Excel 报告。当用户需要一键生成数据报告、
  从原始数据直接输出分析报告时触发。
---

# 数据报告流水线

## 前置条件

需要以下 Skills 已安装：
- data-cleaner v1.0+
- 本 Skill 的脚本位于 /mnt/skills/public/report-pipeline/

## 执行

获取用户上传的文件路径后，直接运行编排脚本：
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `编排 Skill 的 SKILL.md` 这一小节和 `多 Skill 协作工作流` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
