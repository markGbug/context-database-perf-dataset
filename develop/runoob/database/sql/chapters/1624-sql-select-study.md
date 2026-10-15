# SQL：SQL SELECT 语句

- 来源：[SQL SELECT](https://www.runoob.com/sql/sql-select.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：学习笔记
- 章节序号：1624

## 本章内容

SELECT 语句用于从数据库中选取数据。


## SQL SELECT 语句

SELECT 语句用于从数据库中选取数据。

结果被存储在一个结果表中，称为结果集。


### SQL SELECT 语法

```text
SELECT column1, column2, ...
FROM table_name;
```

与

```text
SELECT * FROM table_name;
```

参数说明：

- column1, column2, ...：要选择的字段名称，可以为多个字段。如果不指定字段名称，则会选择所有字段。
- table_name：要查询的表名称。
- *: 通配符，表示选择表中的所有列。


## 演示数据库

在本教程中，我们将使用 RUNOOB 样本数据库。

下面是选自 "Websites" 表的数据：

```text
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝          | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程      | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博          | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+
```


## SELECT Column 实例

下面的 SQL 语句从 "Websites" 表中选取 "name" 和 "country" 列：


## 实例

```text
SELECT name,country FROM Websites;
```

输出结果为:


## SELECT * 实例

下面的 SQL 语句从 "Websites" 表中选取所有列：


## 实例

```text
SELECT * FROM Websites;
```

输出结果为:


## 结果集中的导航

大多数数据库软件系统都允许使用编程函数在结果集中进行导航，比如：Move-To-First-Record、Get-Record-Content、Move-To-Next-Record 等等。

类似这些编程函数不在本教程讲解之列。如需学习通过函数调用访问数据的知识，请访问我们的 ADO 教程 或者 PHP 教程。


## 复习重点

- 能说明 `SQL SELECT` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
