# Skills（技能）：Skill 数据清洗与分析

- 来源：[Skill 数据清洗与分析](https://www.runoob.com/skills/skills-project-data.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：概念卡
- 章节序号：0651

## 本章内容

本项目构建一个数据清洗 Skill，自动处理用户上传的 CSV/Excel 数据，完成清洗、统计和报告生成。

目标：掌握 pandas 数据处理流水线与多步骤 Skill 的设计。


## 项目功能概览


## 目录结构

```text
data-cleaner/
├── SKILL.md
└── scripts/
    ├── requirements.txt
    ├── load_data.py
    ├── quality_check.py
    ├── clean_data.py
    ├── calc_stats.py
    └── gen_report.py
```


## 步骤一：加载数据


## 实例


## 步骤二：质量检测


## 实例


## 步骤三：数据清洗


## 实例


## SKILL.md 完整内容

```text
---
name: data-cleaner
version: 1.0.0
description: >
  清洗并分析用户上传的 CSV/Excel 数据，包含质量检测、去重、
  空值处理、统计分析和报告生成。当用户需要数据清洗、数据预处理、
  统计分析、数据质量报告时触发。
---

# 数据清洗与分析助手

## 执行流程

### 第一步：加载数据
```bash
cd scripts/
python load_data.py <文件路径>
```
告知用户数据规模（行数、列数）和列名。

### 第二步：质量检测
```bash
python quality_check.py /home/claude/loaded_data.csv
```
展示质量报告：有哪些列有空值、有多少重复行、哪些列有异常值。
询问用户：是否按默认规则清洗？或需要自定义处理方式？

### 第三步：执行清洗
用户确认后执行：
```bash
python clean_data.py /home/claude/loaded_data.csv
```
告知清洗结果：删除了多少重复行、填充了多少空值。

### 第四步：输出清洗后的文件
将 /home/claude/cleaned_data.csv 复制到输出目录后调用 present_files 展示。
```


## 记忆卡片

- 一句话定义：`Skill 数据清洗与分析` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
