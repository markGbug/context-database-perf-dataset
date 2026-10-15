# PostgreSQL：PostgreSQL SELECT 语句

- 来源：[PostgreSQL SELECT](https://www.runoob.com/postgresql/postgresql-select.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：学习笔记
- 章节序号：1562

## 本章内容

PostgreSQL SELECT 语句用于从数据库中选取数据。

结果被存储在一个结果表中，称为结果集。


### 语法

SELECT 语句语法格式如下：

```text
SELECT column1, column2,...columnN FROM table_name;
```

- column1, column2,...columnN 为表中字段名。
- table_name 为表名。

如果我们想读取表中的所有数据可以使用以下 SQL 语句：

```text
SELECT * FROM table_name;
```

在上一章节 INSERT INTO 语句 中，我们已经向表 company 插入了一些数据，使用 * 号可以读取该表的所有数据：

```text
runoobdb=# SELECT * FROM company;

ID        NAME        AGE        ADDRESS     SALARY   JOIN_DATE
----      ----------  -----      ----------  -------      --------
1         Paul        32         California  20000.0      2001-07-13
2         Allen       25         Texas                    2007-12-13
3         Teddy       23         Norway      20000.0
4         Mark        25         Rich-Mond   65000.0      2007-12-13
5         David       27         Texas       85000.0      2007-12-13
```

我们也可以读取指定字段 ID 和 NAME：

```text
runoobdb=# SELECT ID,NAME FROM company;
 id | name
----+-------
  1 | Paul
  2 | Allen
  3 | Teddy
  4 | Mark
  5 | David
(5 rows)
```


## 复习重点

- 能说明 `PostgreSQL SELECT` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
