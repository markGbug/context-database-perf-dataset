# 知识点 21636：Skills（技能）：Skills 异步与并发 - 同步 vs 异步：何时该用异步

- 来源：[Skills 异步与并发](https://www.runoob.com/skills/skills-async.html)
- 来源章节：[0646-skills-async-concept.md](../chapters/0646-skills-async-concept.md)
- 分类：AI / 智能开发
- 技术：Skills（技能）
- 所在小节：同步 vs 异步：何时该用异步
- 知识类型：解释
- 原章节序号：0646

## 原文片段

异步不等于并行。Python 的 asyncio 是单线程的事件循环，适合 I/O 密集型任务（等待网络、磁盘）。CPU 密集型任务应使用 ProcessPoolExecutor。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `同步 vs 异步：何时该用异步` 这一小节和 `Skills 异步与并发` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
