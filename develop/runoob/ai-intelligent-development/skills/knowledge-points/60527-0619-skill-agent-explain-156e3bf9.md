# 知识点 60527：Skills（技能）：Skills 目录结构 - Skill 与 Agent 的关系

- 来源：[Skills 目录结构](https://www.runoob.com/skills/skills-dir.html)
- 来源章节：[0619-skills-dir-study.md](../chapters/0619-skills-dir-study.md)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 所在小节：Skill 与 Agent 的关系
- 知识类型：解释
- 原章节序号：0619

## 原文片段

关键要点：Agent 不会一次性加载所有 Skill 的完整内容。它会先读取每个 Skill 的描述信息，命中目标 Skill 后再加载完整内容。这样做的原因是：如果有几百个 Skills，每次都全部加载会极其浪费 Token。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `Skill 与 Agent 的关系` 这一小节和 `Skills 目录结构` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
