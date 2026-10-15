# SQL：SQL RIGHT JOIN 关键字

- 来源：[SQL RIGHT JOIN](https://www.runoob.com/sql/sql-join-right.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：练习笔记
- 章节序号：1641

## 本章内容

RIGHT JOIN 是 SQL 中的一个连接关键字，用于从多个表中提取数据。

与 LEFT JOIN 类似，但其行为相反：RIGHT JOIN 会返回右表中的所有记录，即使左表中没有匹配的记录。

RIGHT JOIN 关键字从右表（table2）返回所有的行，即使左表（table1）中没有匹配。如果左表中没有匹配，则结果为 NULL。


### SQL RIGHT JOIN 语法

```text
SELECT column_name(s)
FROM table1
RIGHT JOIN table2
ON table1.column_name=table2.column_name;
```

或：

```text
SELECT column_name(s)
FROM table1
RIGHT OUTER JOIN table2
ON table1.column_name=table2.column_name;
```

注释：在某些数据库中，RIGHT JOIN 称为 RIGHT OUTER JOIN。

- table1：左表。
- table2：右表，RIGHT JOIN 会保留该表的所有记录。
- ON table1.column_name=table2.column_name：指定连接条件，通常是两个表的共同字段。


### 特点

- 保留右表的所有记录：即使左表中没有匹配的记录，也会在结果中包含右表的所有记录。
- 左表未匹配时填充 NULL：如果左表中没有对应的记录，用 NULL 填充左表的列。

假设有两个表：Employees 和 Departments。

Employees 表：

Departments 表：

```text
SELECT Employees.Name, Departments.DepartmentName
FROM Employees
RIGHT JOIN Departments
ON Employees.DepartmentID = Departments.DepartmentID;
```

查询输出结果：

解释：RIGHT JOIN 返回了 Departments 表中的所有记录。对于 DepartmentID = 30 的记录，由于 Employees 表中没有匹配数据，其 Name 列为 NULL。


### 与 LEFT JOIN 的区别

- LEFT JOIN：返回左表的所有记录，即使右表没有匹配项。
- RIGHT JOIN：返回右表的所有记录，即使左表没有匹配项。


## 演示数据库

在本教程中，我们将使用 RUNOOB 样本数据库。

操作前先在 access_log 表添加一条数据，该数据在 Websites 表没有对应的数据：

```text
INSERT INTO `access_log` (`aid`, `site_id`, `count`, `date`) VALUES ('10', '6', '111', '2016-03-09');
```

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
| 7  | stackoverflow | http://stackoverflow.com/ |   0 | IND     |
+----+---------------+---------------------------+-------+---------+
```

下面是 "access_log" 网站访问记录表的数据：

```text
mysql> SELECT * FROM access_log;
+-----+---------+-------+------------+
| aid | site_id | count | date       |
+-----+---------+-------+------------+
|   1 |       1 |    45 | 2016-05-10 |
|   2 |       3 |   100 | 2016-05-13 |
|   3 |       1 |   230 | 2016-05-14 |
|   4 |       2 |    10 | 2016-05-14 |
|   5 |       5 |   205 | 2016-05-14 |
|   6 |       4 |    13 | 2016-05-15 |
|   7 |       3 |   220 | 2016-05-15 |
|   8 |       5 |   545 | 2016-05-16 |
|   9 |       3 |   201 | 2016-05-17 |
|  10 |       6 |   111 | 2016-03-19 |
+-----+---------+-------+------------+
9 rows in set (0.00 sec)
```


## SQL RIGHT JOIN 实例

下面的 SQL 语句将返回网站的访问记录。

以下实例中我们把 Websites 作为左表，access_log 作为右表：


## 实例

```text
SELECT websites.name, access_log.count, access_log.date
FROM websites
RIGHT JOIN access_log
ON access_log.site_id=websites.id
ORDER BY access_log.count DESC;
```

执行以上 SQL 输出结果如下：

注释：RIGHT JOIN 关键字从右表（access_log）返回所有的行，即使左表（Websites）中没有匹配。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQL RIGHT JOIN` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
