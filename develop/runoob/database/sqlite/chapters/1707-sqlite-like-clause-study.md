# SQLite：SQLite Like 子句

- 来源：[SQLite Like 子句](https://www.runoob.com/sqlite/sqlite-like-clause.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：学习笔记
- 章节序号：1707

## 本章内容

SQLite 的 LIKE 运算符是用来匹配通配符指定模式的文本值。如果搜索表达式与模式表达式匹配，LIKE 运算符将返回真（true），也就是 1。这里有两个通配符与 LIKE 运算符一起使用：

- 百分号 （%）
- 下划线 （_）

百分号（%）代表零个、一个或多个数字或字符。下划线（_）代表一个单一的数字或字符。这些符号可以被组合使用。


## 语法

% 和 _ 的基本语法如下：

```text
SELECT column_list
FROM table_name
WHERE column LIKE 'XXXX%'

or

SELECT column_list
FROM table_name
WHERE column LIKE '%XXXX%'

or

SELECT column_list
FROM table_name
WHERE column LIKE 'XXXX_'

or

SELECT column_list
FROM table_name
WHERE column LIKE '_XXXX'

or

SELECT column_list
FROM table_name
WHERE column LIKE '_XXXX_'
```

您可以使用 AND 或 OR 运算符来结合 N 个数量的条件。在这里，XXXX 可以是任何数字或字符串值。


## 实例

下面一些实例演示了 带有 '%' 和 '_' 运算符的 LIKE 子句不同的地方：

让我们举一个实际的例子，假设 COMPANY 表有以下记录：

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

下面是一个实例，它显示 COMPANY 表中 AGE 以 2 开头的所有记录：

```text
sqlite> SELECT * FROM COMPANY WHERE AGE  LIKE '2%';
```

这将产生以下结果：

```text
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
```

下面是一个实例，它显示 COMPANY 表中 ADDRESS 文本里包含一个连字符（-）的所有记录：

```text
sqlite> SELECT * FROM COMPANY WHERE ADDRESS  LIKE '%-%';
```

这将产生以下结果：

```text
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
4           Mark        25          Rich-Mond   65000.0
6           Kim         22          South-Hall  45000.0
```


## 复习重点

- 能说明 `SQLite Like 子句` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
