# MySQL：MySQL 查询数据

- 来源：[MySQL 查询数据](https://www.runoob.com/mysql/mysql-select-query.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：学习笔记
- 章节序号：1518

## 本章内容

MySQL 数据库使用 SELECT 语句来查询数据。

你可以通过 mysql> 命令提示窗口中在数据库中查询数据，或者通过 PHP 脚本来查询数据。


### 语法

以下为在 MySQL 数据库中查询数据通用的 SELECT 语法：

```text
SELECT column1, column2, ...
FROM table_name
[WHERE condition]
[ORDER BY column_name [ASC | DESC]]
[LIMIT number];
```

参数说明：

- column1, column2, ... 是你想要选择的列的名称，如果使用 * 表示选择所有列。
- table_name 是你要从中查询数据的表的名称。
- WHERE condition 是一个可选的子句，用于指定过滤条件，只返回符合条件的行。
- ORDER BY column_name [ASC | DESC] 是一个可选的子句，用于指定结果集的排序顺序，默认是升序（ASC）。
- LIMIT number 是一个可选的子句，用于限制返回的行数。

MySQL SELECT 语句简单的应用实例：


## 实例

SELECT 语句可以是灵活的，我们可以根据实际需求组合和使用这些子句，比如同时使用 WHERE 和 ORDER BY 子句，或者使用 LIMIT 控制返回的行数。

在 WHERE 子句中，你可以使用各种条件运算符（如 =, <, >, <=, >=, !=），逻辑运算符（如 AND, OR, NOT），以及通配符（如 %）等。

以下是一些进阶的 SELECT 语句实例：


## 实例


## 通过命令提示符获取数据

以下实例我们将通过 SQL SELECT 命令来获取 MySQL 数据表 runoob_tbl 的数据：


### 实例

以下实例将返回数据表 runoob_tbl 的所有记录:


## 读取数据表：

```text
select * from runoob_tbl;
```

输出结果：


## 使用 PHP 脚本来获取数据

使用 PHP 函数的 mysqli_query() 及 SQL SELECT 命令来获取数据。

该函数用于执行 SQL 命令，然后通过 PHP 函数 mysqli_fetch_array() 来使用或输出所有查询的数据。

mysqli_fetch_array() 函数从结果集中取得一行作为关联数组，或数字数组，或二者兼有 返回根据从结果集取得的行生成的数组，如果没有更多行则返回 false。

以下实例为从数据表 runoob_tbl 中读取所有记录。


### 实例


## 复习重点

- 能说明 `MySQL 查询数据` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
