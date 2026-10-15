# PostgreSQL：PostgreSQL 表达式

- 来源：[PostgreSQL 表达式](https://www.runoob.com/postgresql/postgresql-expressions.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：练习笔记
- 章节序号：1564

## 本章内容

表达式是由一个或多个的值、运算符、PostgresSQL 函数组成的。

PostgreSQL 表达式类似一个公式，我们可以将其应用在查询语句中，用来查找数据库中指定条件的结果集。


### 语法

SELECT 语句的语法格式如下：

```text
SELECT column1, column2, columnN
FROM table_name
WHERE [CONDITION | EXPRESSION];
```

PostgreSQL 的表达式可以有不同类型，我们接下来会讲到。


### 布尔表达式

布尔表达式是根据一个指定条件来读取数据：

```text
SELECT column1, column2, columnN
FROM table_name
WHERE SINGLE VALUE MATCHTING EXPRESSION;
```

创建 COMPANY 表（下载 COMPANY SQL 文件 ），数据内容如下：

```text
runoobdb# select * from COMPANY;
 id | name  | age | address   | salary
----+-------+-----+-----------+--------
  1 | Paul  |  32 | California|  20000
  2 | Allen |  25 | Texas     |  15000
  3 | Teddy |  23 | Norway    |  20000
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
  6 | Kim   |  22 | South-Hall|  45000
  7 | James |  24 | Houston   |  10000
(7 rows)
```

以下使用了布尔表达式（SALARY=10000）来查询数据：

```text
runoobdb=# SELECT * FROM COMPANY WHERE SALARY = 10000;
 id | name  | age | address  | salary
----+-------+-----+----------+--------
  7 | James |  24 | Houston  |  10000
(1 row)
```


### 数字表达式

数字表达式常用于查询语句中的数学运算：

```text
SELECT numerical_expression as  OPERATION_NAME
[FROM table_name WHERE CONDITION] ;
```

numerical_expression 是一个数学运算表达式，实例如下：

```text
runoobdb=# SELECT (17 + 6) AS ADDITION ;
 addition
----------
       23
(1 row)
```

此外 PostgreSQL 还内置了一些数学函数，如：

- avg() ： 返回一个表达式的平均值
- sum() ： 返回指定字段的总和
- count() ： 返回查询的记录总数

以下实例查询 COMPANY 表的记录总数：

```text
runoobdb=# SELECT COUNT(*) AS "RECORDS" FROM COMPANY;
 RECORDS
---------
       7
(1 row)
```


### 日期表达式

日期表达式返回当前系统的日期和时间，可用于各种数据操作，以下实例查询当前时间：

```text
runoobdb=# SELECT CURRENT_TIMESTAMP;
       current_timestamp
-------------------------------
 2019-06-13 10:49:06.419243+08
(1 row)
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PostgreSQL 表达式` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
