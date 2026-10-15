# MySQL：MySQL 复制表

- 来源：[MySQL 复制表](https://www.runoob.com/mysql/mysql-clone-tables.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：学习笔记
- 章节序号：1533

## 本章内容

如果我们需要完全的复制 MySQL 的数据表，包括表的结构，索引，默认值等。

如果仅仅使用 CREATE TABLE ... SELECT 命令，是无法实现的。

本章节将为大家介绍如何完整的复制 MySQL 数据表，步骤如下：

- 使用 SHOW CREATE TABLE 命令获取创建数据表(CREATE TABLE) 语句，该语句包含了原数据表的结构，索引等。


## 复习重点

- 能说明 `MySQL 复制表` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
