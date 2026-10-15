# 知识点 81155：Redis：Redis 分区 - 分区类型

- 来源：[Redis 分区](https://www.runoob.com/redis/redis-partitioning.html)
- 来源章节：[1618-redis-partitioning-practice.md](../chapters/1618-redis-partitioning-practice.md)
- 分类：数据库
- 技术：Redis
- 所在小节：分区类型
- 知识类型：解释
- 原章节序号：1618

## 原文片段

Redis 有两种类型分区。假设有4个Redis实例 R0，R1，R2，R3，和类似user:1，user:2这样的表示用户的多个key，对既定的key有多种不同方式来选择这个key存放在哪个实例中。也就是说，有不同的系统来映射某个key到某个Redis服务。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `分区类型` 这一小节和 `Redis 分区` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
