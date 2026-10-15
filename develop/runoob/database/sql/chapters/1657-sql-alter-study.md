# SQL：SQL ALTER TABLE 语句

- 来源：[SQL ALTER](https://www.runoob.com/sql/sql-alter.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：学习笔记
- 章节序号：1657

## 本章内容

## ALTER TABLE 语句

ALTER TABLE 语句用于在已有的表中添加、删除或修改列。


### SQL ALTER TABLE 语法

如需在表中添加列，请使用下面的语法:

如需删除表中的列，请使用下面的语法（请注意，某些数据库系统不允许这种在数据库表中删除列的方式）：

要改变表中列的数据类型，请使用下面的语法：

SQL Server / MS Access：

My SQL / Oracle：

Oracle 10G 之后版本:

```text
ALTER TABLE table_name
MODIFY column_name datatype;
```


## SQL ALTER TABLE 实例

请看 "Persons" 表：

现在，我们想在 "Persons" 表中添加一个名为 "DateOfBirth" 的列。

我们使用下面的 SQL 语句：

请注意，新列 "DateOfBirth" 的类型是 date，可以存放日期。数据类型规定列中可以存放的数据的类型。如需了解 MS Access、MySQL 和 SQL Server 中可用的数据类型，请访问我们完整的 数据类型参考手册。

现在，"Persons" 表将如下所示：


## 改变数据类型实例

现在，我们想要改变 "Persons" 表中 "DateOfBirth" 列的数据类型。

我们使用下面的 SQL 语句：

请注意，现在 "DateOfBirth" 列的类型是 year，可以存放 2 位或 4 位格式的年份。


## DROP COLUMN 实例

接下来，我们想要删除 "Person" 表中的 "DateOfBirth" 列。

我们使用下面的 SQL 语句：

现在，"Persons" 表将如下所示：


## 复习重点

- 能说明 `SQL ALTER` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
