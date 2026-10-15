# Skills（技能）：多 Skill 协作工作流

- 来源：[多 Skill 协作工作流](https://www.runoob.com/skills/skills-project-multi.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：学习笔记
- 章节序号：0652

## 本章内容

本项目将前三个实战项目整合为一个完整的"数据报告生成"工作流。

目标：掌握多 Skill 编排，以及如何设计一个统筹全局的编排 Skill。


## 工作流目标

用户上传一份业务数据文件，系统自动完成以下全链路工作，最终交付一份完整的业务报告。


## 编排 Skill 的设计原则

编排 Skill 不做具体的业务处理，只负责调度其他 Skill 的输出、传递中间结果、在关键节点向用户汇报进度。


## 编排脚本


## 实例

```text
【1/3】正在清洗数据...
  已清洗：删除重复行 5 条，填充空值 18 处
【2/3】正在生成统计报告...
【3/3】正在生成 Excel 报告...
{
  "status": "success",
  "output": "/mnt/user-data/outputs/runoob_sales_report.xlsx",
  "clean_stats": {"dup_removed": 5, "nulls_filled": 18}
}
```


## 编排 Skill 的 SKILL.md

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

```bash
python scripts/orchestrator.py <文件路径>
```

脚本会实时输出每阶段的进度，完成后输出最终文件路径。
解析 JSON 输出后调用 present_files 展示报告文件。

## 失败处理

若任意阶段失败，输出包含 stage 和 message 的错误信息，
告知用户是哪个阶段失败以及可能的原因，不要继续执行后续阶段。
```


## 复习重点

- 能说明 `多 Skill 协作工作流` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
