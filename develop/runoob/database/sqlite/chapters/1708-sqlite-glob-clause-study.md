# SQLite：SQLite Glob 子句

- 来源：[SQLite Glob 子句](https://www.runoob.com/sqlite/sqlite-glob-clause.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：学习笔记
- 章节序号：1708

## 本章内容

SQLite 的 GLOB 运算符是用来匹配通配符指定模式的文本值。如果搜索表达式与模式表达式匹配，GLOB 运算符将返回真（true），也就是 1。与 LIKE 运算符不同的是，GLOB 是大小写敏感的，对于下面的通配符，它遵循 UNIX 的语法。

- *：匹配零个、一个或多个数字或字符。
- ?：代表一个单一的数字或字符。
- [...]：匹配方括号内指定的字符之一。例如，[abc] 匹配 "a"、"b" 或 "c" 中的任何一个字符。
- [^...]：匹配不在方括号内指定的字符之一。例如，[^abc] 匹配不是 "a"、"b" 或 "c" 中的任何一个字符的字符。

以上这些符号可以被组合使用。


## 语法

* 和 ? 的基本语法如下：

```text
SELECT FROM table_name
WHERE column GLOB 'XXXX*'

or

SELECT FROM table_name
WHERE column GLOB '*XXXX*'

or

SELECT FROM table_name
WHERE column GLOB 'XXXX?'

or

SELECT FROM table_name
WHERE column GLOB '?XXXX'

or

SELECT FROM table_name
WHERE column GLOB '?XXXX?'

or

SELECT FROM table_name
WHERE column GLOB '????'
```

您可以使用 AND 或 OR 运算符来结合 N 个数量的条件。在这里，XXXX 可以是任何数字或字符串值。


## 实例

下面一些实例演示了 带有 '*' 和 '?' 运算符的 GLOB 子句不同的地方：

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
sqlite> SELECT * FROM COMPANY WHERE AGE  GLOB '2*';
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
sqlite> SELECT * FROM COMPANY WHERE ADDRESS  GLOB '*-*';
```

这将产生以下结果：

```text
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
4           Mark        25          Rich-Mond   65000.0
6           Kim         22          South-Hall  45000.0
```


### [...] 通配符

[...] 表达式用于匹配方括号内指定的字符集中的任何一个字符。

实例 1：匹配以 "A" 或 "B" 开头的产品名称。

```text
SELECT * FROM products WHERE product_name LIKE '[AB]%';
```

这将匹配以 "A" 或 "B" 开头的产品名称。

实例 2：匹配以 "1"、"2" 或 "3" 开头的电话号码。

```text
SELECT * FROM customers WHERE phone_number LIKE '[123]%';
```

这将匹配以 "1"、"2" 或 "3" 开头的电话号码。


### [^...] 通配符

[^...] 表达式用于匹配不在方括号内指定的字符集中的任何字符。

实例 1：匹配不以 "X" 或 "Y" 开头的产品代码。

```text
SELECT * FROM products WHERE product_code LIKE '[^XY]%';
```

这将匹配不以 "X" 或 "Y" 开头的产品代码。 实例 2：匹配不包含数字字符的用户名。

```text
SELECT * FROM users WHERE username LIKE '[^0-9]%';
```

这将匹配不以数字字符开头的用户名。


## 复习重点

- 能说明 `SQLite Glob 子句` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
