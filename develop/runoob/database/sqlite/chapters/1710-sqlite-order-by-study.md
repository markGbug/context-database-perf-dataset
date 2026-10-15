# SQLite：SQLite Order By

- 来源：[SQLite Order By](https://www.runoob.com/sqlite/sqlite-order-by.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：学习笔记
- 章节序号：1710

## 本章内容

SQLite 的 ORDER BY 子句是用来基于一个或多个列按升序或降序顺序排列数据。


## 语法

ORDER BY 子句的基本语法如下：

```text
SELECT column-list
FROM table_name
[WHERE condition]
[ORDER BY column1, column2, .. columnN] [ASC | DESC];
```

- ASC 默认值，从小到大，升序排列
- DESC 从大到小，降序排列

您可以在 ORDER BY 子句中使用多个列，确保您使用的排序列在列清单中：

```text
SELECT
   select_list
FROM
   table
ORDER BY
    column_1 ASC,
    column_2 DESC;
```

column_1 与 column_2 如果后面不指定排序规则，默认为 ASC 升序，以上语句按 column_1 升序，column_2 降序读取，等价如下语句：

```text
SELECT
   select_list
FROM
   table
ORDER BY
    column_1,
    column_2 DESC;
```


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

下面是一个实例，它会将结果按 SALARY 升序排序：

```text
sqlite> SELECT * FROM COMPANY ORDER BY SALARY ASC;
```

这将产生以下结果：

```text
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
7           James       24          Houston     10000.0
2           Allen       25          Texas       15000.0
1           Paul        32          California  20000.0
3           Teddy       23          Norway      20000.0
6           Kim         22          South-Hall  45000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
```

下面是一个实例，它会将结果按 NAME 和 SALARY 升序排序：

```text
sqlite> SELECT * FROM COMPANY ORDER BY NAME, SALARY ASC;
```

这将产生以下结果：

```text
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
2           Allen       25          Texas       15000.0
5           David       27          Texas       85000.0
7           James       24          Houston     10000.0
6           Kim         22          South-Hall  45000.0
4           Mark        25          Rich-Mond   65000.0
1           Paul        32          California  20000.0
3           Teddy       23          Norway      20000.0
```

下面是一个实例，它会将结果按 NAME 降序排序：

```text
sqlite> SELECT * FROM COMPANY ORDER BY NAME DESC;
```

这将产生以下结果：

```text
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
3           Teddy       23          Norway      20000.0
1           Paul        32          California  20000.0
4           Mark        25          Rich-Mond   65000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
5           David       27          Texas       85000.0
2           Allen       25          Texas       15000.0
```


## 复习重点

- 能说明 `SQLite Order By` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
