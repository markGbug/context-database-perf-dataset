# 知识点 43392：Redis：Redis HyperLogLog - 什么是基数?

- 来源：[Redis HyperLogLog](https://www.runoob.com/redis/redis-hyperloglog.html)
- 来源章节：[1605-redis-hyperloglog-practice.md](../chapters/1605-redis-hyperloglog-practice.md)
- 分类：数据库
- 技术：Redis
- 所在小节：什么是基数?
- 知识类型：解释
- 原章节序号：1605

## 原文片段

比如数据集 {1, 3, 5, 7, 5, 7, 8}， 那么这个数据集的基数集为 {1, 3, 5 ,7, 8}, 基数(不重复元素)为5。基数估计就是在误差可接受的范围内，快速计算基数。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `什么是基数?` 这一小节和 `Redis HyperLogLog` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
