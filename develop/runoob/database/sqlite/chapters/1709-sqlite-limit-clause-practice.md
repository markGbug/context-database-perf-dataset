# SQLite：SQLite Limit 子句

- 来源：[SQLite Limit 子句](https://www.runoob.com/sqlite/sqlite-limit-clause.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：练习笔记
- 章节序号：1709

## 本章内容

SQLite 的 LIMIT 子句用于限制由 SELECT 语句返回的数据数量。


## 语法

带有 LIMIT 子句的 SELECT 语句的基本语法如下：

```text
SELECT column1, column2, columnN
FROM table_name
LIMIT [no of rows]
```

下面是 LIMIT 子句与 OFFSET 子句一起使用时的语法：

```text
SELECT column1, column2, columnN
FROM table_name
LIMIT [no of rows] OFFSET [row num]
```

以上 SQL 语句从 table_name 表中选择column1、column2等列的数据，并且限制返回的行数和起始行，通常用于分页显示数据，其中LIMIT用于控制每页显示的行数，OFFSET用于控制从哪一行开始显示数据。

- SELECT column1, column2, columnN：这部分指定了要从数据库中选择哪些列。column1、column2 和 columnN 是列的名称，你可以替换成实际的列名。columnN 表示可能还有更多的列，这里用 N 表示列的数量是可变的。
- FROM table_name：这部分指定了要从哪个表中查询数据。table_name 应该替换成实际的表名。
- LIMIT [no of rows]：这部分用来限制查询结果的行数。[no of rows] 是一个数字，表示你想要返回的最大行数。例如，如果你写 LIMIT 10，那么查询将只返回最多10行数据。
- OFFSET [row num]：这部分用来指定查询结果的起始点。[row num] 是一个数字，表示从哪一行开始返回数据。例如，如果你写 OFFSET 5，那么查询将跳过前5行数据，从第6行开始返回数据。


## 实例

假设 COMPANY 表有以下记录：

```text
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
```

下面是一个实例，它限制了您想要从表中提取的行数：

```text
sqlite> SELECT * FROM COMPANY LIMIT 6;
```

这将产生以下结果：

```text
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
```

但是，在某些情况下，可能需要从一个特定的偏移开始提取记录。下面是一个实例，从第三位开始提取 3 个记录：

```text
sqlite> SELECT * FROM COMPANY LIMIT 3 OFFSET 2;
```

这将产生以下结果：

```text
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQLite Limit 子句` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
