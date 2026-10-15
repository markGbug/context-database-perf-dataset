# Skills（技能）：Skills 触发机制

- 来源：[Skills 触发机制](https://www.runoob.com/skills/skills-trigger.html)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 笔记类型：概念卡
- 章节序号：0628

## 本章内容

Skills 不是被用户"调用"的，而是由 Claude 自主决定"是否使用"的。

理解这个触发机制，能帮助你写出更容易被准确触发的 Skill。


## 触发机制的工作原理

Claude 启动时，会将所有可用 Skill 的 name 和 description 加载到上下文中。

当用户发送消息后，Claude 会判断：这个任务，我需要参考某个 Skill 吗？

判断依据只有一个：Skill 的 description 字段。

SKILL.md 的正文（body）不参与触发判断。Claude 只有在决定使用某个 Skill 之后，才会读取正文内容。


### 触发流程示意


## 什么样的任务会触发 Skill

并非所有匹配 description 的请求都会触发 Skill。

Claude 有一个内在判断：这个任务复杂到需要参考专门指令吗？

如果你的 Skill 很少被触发，通常是因为任务描述过于简单，或者 description 写得不够精准。测试时应使用复杂、具体的用户请求。


## Description 的触发策略

description 是触发的唯一凭据，写法直接决定触发准确率。


### 策略一：列举具体场景

不要只写"这个 Skill 是做什么的"，还要写"在什么情况下应该用它"。

```text
# 不推荐：只描述功能
description: 处理 Excel 文件。

# 推荐：描述功能 + 触发场景
description: >
  处理 Excel 和 CSV 文件，包括：读取数据、清洗格式、生成图表、
  计算统计指标、合并多个表格。当用户提到 Excel、xlsx、CSV、
  表格数据、数据清洗、财务报表时，应优先使用此 Skill。
```


### 策略二：使用"推动性"语言

Skills 系统天然倾向于"少触发"。在 description 中加入推动性语言可以提升触发率。

```java
description: >
  生成专业的 PowerPoint 演示文稿。当用户需要制作幻灯片、PPT、演讲稿、
  汇报材料时，必须使用此 Skill，即使用户没有明确说"用 pptx 格式"。
  只要涉及演示文稿的创建或修改，都应触发此 Skill。
```


### 策略三：列出关键词

在 description 末尾附上触发关键词列表，是一种简单有效的补充手段。

```text
description: >
  代码审查助手，分析代码质量、发现潜在 Bug、给出改进建议。
  关键词：code review、代码审查、代码分析、bug 检查、
  重构建议、代码质量、静态分析。
```


## 触发冲突：多个 Skill 同时匹配

当用户的请求可能匹配多个 Skill 时，Claude 会根据匹配程度选择最相关的一个。

为了避免冲突，需要让不同 Skill 的 description 保持清晰的边界。

Skill 的 description 应当"排他性"地描述自己的适用场景，而不仅仅是描述自己"能做什么"。能做什么 ≠ 应该什么时候用。


## 使用 Description 优化工具测试触发

skill-creator Skill 提供了一个 description 优化脚本，可以自动评估触发准确率。


## 实例

脚本会自动运行测试、评估得分、修改 description，并输出最优结果。

详细的 description 优化方法参见第 24 篇：Skills 描述优化技巧。


## 记忆卡片

- 一句话定义：`Skills 触发机制` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
