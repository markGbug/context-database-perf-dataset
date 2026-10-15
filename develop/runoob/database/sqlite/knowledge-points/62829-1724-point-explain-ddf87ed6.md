# 知识点 62829：SQLite：SQLite Truncate Table - 语法

- 来源：[SQLite Truncate Table](https://www.runoob.com/sqlite/sqlite-truncate-table.html)
- 来源章节：[1724-sqlite-truncate-table-practice.md](../chapters/1724-sqlite-truncate-table-practice.md)
- 分类：数据库
- 技术：SQLite
- 所在小节：语法
- 知识类型：解释
- 原章节序号：1724

## 原文片段

当 SQLite 数据库中包含自增列时，会自动建立一个名为 sqlite_sequence 的表。这个表包含两个列：name 和 seq。name 记录自增列所在的表，seq 记录当前序号（下一条记录的编号就是当前序号加 1）。如果想把某个自增列的序号归零，只需要修改 sqlite_sequence 表就可以了。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `语法` 这一小节和 `SQLite Truncate Table` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
