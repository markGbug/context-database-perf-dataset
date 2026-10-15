# SQL：SQL FULL OUTER JOIN 关键字

- 来源：[SQL FULL JOIN](https://www.runoob.com/sql/sql-join-full.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：练习笔记
- 章节序号：1642

## 本章内容

FULL OUTER JOIN 是 SQL 中的一种连接方式，用于同时保留两个表中所有的记录，即使其中一方没有匹配项。

FULL OUTER JOIN 结果包括两个表中满足条件的记录（交集部分）以及不满足条件的记录（并集中的非交集部分）。 如果某条记录在一张表中存在，而在另一张表中没有匹配项，则该记录的缺失列会以 NULL 填充。

FULL OUTER JOIN 关键字只要左表（table1）和右表（table2）其中一个表中存在匹配，则返回行。

FULL OUTER JOIN 关键字结合了 LEFT JOIN 和 RIGHT JOIN 的结果。


### SQL FULL OUTER JOIN 语法

```text
SELECT column_name(s)
FROM table1
FULL OUTER JOIN table2
ON table1.column_name=table2.column_name;
```

- table1、table2：需要进行连接的两个表。
- ON table1.column_name=table2.column_name：指定连接条件，通常是两个表的共同字段。
- column_name(s) ：从两个表中选择需要的字段。


### 特点

- 返回两个表的并集：包含所有匹配和未匹配的记录。
- 未匹配的记录填充 NULL：如果某条记录在一张表中没有匹配项，则其对应的字段以 NULL 表示。
- 对等性：FULL OUTER JOIN 包含了 LEFT JOIN 和 RIGHT JOIN 的结果。

假设有两个表：Students 和 Courses。

Students 表：

Courses 表：

```text
SELECT Students.StudentID, Students.Name, Courses.CourseName
FROM Students
FULL OUTER JOIN Courses
ON Students.StudentID = Courses.StudentID;
```

查询输出结果：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQL FULL JOIN` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
