# Skills（技能）：Skills 描述优化技巧

- 来源：[Skills 描述优化技巧](https://www.runoob.com/skills/skills-description-optimize.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：学习笔记
- 章节序号：0640

## 本章内容

description 字段是 Skill 触发的唯一判断依据。

一个写得好的 description，能让 Skill 在正确的时机被触发，并避免在不相关的场景下干扰 Claude。


## Description 的作用与限制

Claude 在决定是否使用某个 Skill 时，只会阅读 description 字段，不会提前读取 SKILL.md 正文。

这意味着 description 需要同时承担两件事：说明 Skill 能做什么，以及指明何时应该用它。

description 的理想长度是 50-150 字。太短会导致触发不准确，太长则可能超出上下文限制，且 Claude 难以快速扫描比对。


## Description 的四要素结构

```text
---
name: data-analyzer
description: >
  处理 Excel（.xlsx）和 CSV 格式的表格数据，包括数据读取、
  清洗去重、统计分析（均值/中位数/分布）、生成可视化报告。
  当用户需要分析数据文件、生成统计报告、处理表格、
  查找数据规律时应优先使用此 Skill，即使用户只是上传了
  一个数据文件并询问"帮我看看这个"。
---
```


## 常见的 Description 写法问题


## 用自动化工具优化 Description

skill-creator 提供了 description 自动优化脚本，通过迭代测试找出触发率最高的写法。


### 第一步：准备测试用例


## 实例


### 第二步：运行优化循环


## 实例

```text
迭代 1：训练集得分 0.62，测试集得分 0.60
迭代 2：训练集得分 0.75，测试集得分 0.72
迭代 3：训练集得分 0.87，测试集得分 0.85
迭代 4：训练集得分 0.90，测试集得分 0.88
迭代 5：训练集得分 0.91，测试集得分 0.89

最优 description（测试集得分 0.89）已保存。
```


### 第三步：应用最优结果


## 实例


## A/B 对比测试

在不确定哪种写法更好时，可以对两个版本的 description 进行盲测对比。


## 实例

评估应以测试集得分为准，而不是训练集得分。训练集得分高但测试集低，说明 description 过度拟合了测试用例，在真实场景中效果可能变差。


## 复习重点

- 能说明 `Skills 描述优化技巧` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
