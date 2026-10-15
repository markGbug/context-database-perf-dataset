# PostgreSQL：PostgreSQL 运算符

- 来源：[PostgreSQL 运算符](https://www.runoob.com/postgresql/postgresql-operators.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：练习笔记
- 章节序号：1563

## 本章内容

运算符是一种告诉编译器执行特定的数学或逻辑操作的符号。

PostgreSQL 运算符是一个保留关键字或字符，一般用在 WHERE 语句中，作为过滤条件。

常见的运算符有：

- 算术运算符
- 比较运算符
- 逻辑运算符
- 按位运算符


## 算术运算符

假设变量 a 为 2，变量 b 为 3，则：


### 实例

```text
runoobdb=# select 2+3;
 ?column?
----------
        5
(1 row)


runoobdb=# select 2*3;
 ?column?
----------
        6
(1 row)


runoobdb=# select 10/5;
 ?column?
----------
        2
(1 row)


runoobdb=# select 12%5;
 ?column?
----------
        2
(1 row)


runoobdb=# select 2^3;
 ?column?
----------
        8
(1 row)


runoobdb=# select |/ 25.0;
 ?column?
----------
        5
(1 row)


runoobdb=# select ||/ 27.0;
 ?column?
----------
        3
(1 row)


runoobdb=# select 5 !;
 ?column?
----------
      120
(1 row)


runoobdb=# select !!5;
 ?column?
----------
      120
(1 row)
```


## 比较运算符

假设变量 a 为 10，变量 b 为 20，则：


### 实例

创建 COMPANY 表（下载 COMPANY SQL 文件 ），数据内容如下：

```text
runoobdb=# select * from COMPANY;
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

读取 SALARY 字段大于 50000 的数据：

```text
runoobdb=# SELECT * FROM COMPANY WHERE SALARY > 50000;
 id | name  | age |address    | salary
----+-------+-----+-----------+--------
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
(2 rows)
```

读取 SALARY 字段等于 20000 的数据：

```text
runoobdb=#  SELECT * FROM COMPANY WHERE SALARY = 20000;
 id | name  | age |  address    | salary
 ----+-------+-----+-------------+--------
   1 | Paul  |  32 | California  |  20000
   3 | Teddy |  23 | Norway      |  20000
(2 rows)
```

读取 SALARY 字段不等于 20000 的数据：

```text
runoobdb=#  SELECT * FROM COMPANY WHERE SALARY != 20000;
 id | name  | age |  address    | salary
----+-------+-----+-------------+--------
  2 | Allen |  25 | Texas       |  15000
  4 | Mark  |  25 | Rich-Mond   |  65000
  5 | David |  27 | Texas       |  85000
  6 | Kim   |  22 | South-Hall  |  45000
  7 | James |  24 | Houston     |  10000
(5 rows)

runoobdb=# SELECT * FROM COMPANY WHERE SALARY <> 20000;
 id | name  | age | address    | salary
----+-------+-----+------------+--------
  2 | Allen |  25 | Texas      |  15000
  4 | Mark  |  25 | Rich-Mond  |  65000
  5 | David |  27 | Texas      |  85000
  6 | Kim   |  22 | South-Hall |  45000
  7 | James |  24 | Houston    |  10000
(5 rows)
```

读取 SALARY 字段大于等于 65000 的数据：

```text
runoobdb=# SELECT * FROM COMPANY WHERE SALARY >= 65000;
 id | name  | age |  address  | salary
----+-------+-----+-----------+--------
  4 | Mark  |  25 | Rich-Mond |  65000
  5 | David |  27 | Texas     |  85000
(2 rows)
```


## 逻辑运算符

PostgreSQL 逻辑运算符有以下几种：

AND

逻辑与运算符。如果两个操作数都非零，则条件为真。

PostgresSQL 中的 WHERE 语句可以用 AND 包含多个过滤条件。

NOT

逻辑非运算符。用来逆转操作数的逻辑状态。如果条件为真则逻辑非运算符将使其为假。

OR

逻辑或运算符。如果两个操作数中有任意一个非零，则条件为真。

PostgresSQL 中的 WHERE 语句可以用 OR 包含多个过滤条件。

SQL 使用三值的逻辑系统，包括 true、false 和 null，null 表示"未知"。


### 实例

创建 COMPANY 表（下载 COMPANY SQL 文件 ），数据内容如下：

```text
runoobdb=# select * from COMPANY;
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

读取 AGE 字段大于等于 25 且 SALARY 字段大于等于 6500 的数据：

```text
runoobdb=# SELECT * FROM COMPANY WHERE AGE >= 25 AND SALARY >= 6500;
 id | name  | age |                      address                  | salary
----+-------+-----+-----------------------------------------------+--------
  1 | Paul  |  32 | California                                    |  20000
  2 | Allen |  25 | Texas                                         |  15000
  4 | Mark  |  25 | Rich-Mond                                     |  65000
  5 | David |  27 | Texas                                         |  85000
(4 rows)
```

读取 AGE 字段大于等于 25 或 SALARY 字段大于 6500 的数据：

```text
runoobdb=# SELECT * FROM COMPANY WHERE AGE >= 25 OR SALARY >= 6500;
 id | name  | age |  address    | salary
----+-------+-----+-------------+--------
  1 | Paul  |  32 | California  |  20000
  2 | Allen |  25 | Texas       |  15000
  3 | Teddy |  23 | Norway      |  20000
  4 | Mark  |  25 | Rich-Mond   |  65000
  5 | David |  27 | Texas       |  85000
  6 | Kim   |  22 | South-Hall  |  45000
  7 | James |  24 | Houston     |  10000
  8 | Paul  |  24 | Houston     |  20000
  9 | James |  44 | Norway      |   5000
 10 | James |  45 | Texas       |   5000
(10 rows)
```

读取 SALARY 字段不为 NULL 的数据：

```text
runoobdb=#  SELECT * FROM COMPANY WHERE SALARY IS NOT NULL;
 id | name  | age |  address    | salary
----+-------+-----+-------------+--------
  1 | Paul  |  32 | California  |  20000
  2 | Allen |  25 | Texas       |  15000
  3 | Teddy |  23 | Norway      |  20000
  4 | Mark  |  25 | Rich-Mond   |  65000
  5 | David |  27 | Texas       |  85000
  6 | Kim   |  22 | South-Hall  |  45000
  7 | James |  24 | Houston     |  10000
  8 | Paul  |  24 | Houston     |  20000
  9 | James |  44 | Norway      |   5000
 10 | James |  45 | Texas       |   5000
(10 rows)
```


## 位运算符

位运算符作用于位，并逐位执行操作。&、 | 和 ^ 的真值表如下所示：

假设如果 A = 60，且 B = 13，现在以二进制格式表示，它们如下所示：

A = 0011 1100

B = 0000 1101

-----------------

A&B = 0000 1100

A|B = 0011 1101

A^B = 0011 0001

~A = 1100 0011

下表显示了 PostgreSQL 支持的位运算符。假设变量 A 的值为 60，变量 B 的值为 13，则：

按位与操作，按二进制位进行"与"运算。运算规则：

```text
0&0=0;
0&1=0;
1&0=0;
1&1=1;
```

按位或运算符，按二进制位进行"或"运算。运算规则：

```text
0|0=0;
0|1=1;
1|0=1;
1|1=1;
```

异或运算符，按二进制位进行"异或"运算。运算规则：

```text
0#0=0;
0#1=1;
1#0=1;
1#1=0;
```

取反运算符，按二进制位进行"取反"运算。运算规则：

```text
~1=0;
~0=1;
```


### 实例

```text
runoobdb=# select 60 | 13;
 ?column?
----------
       61
(1 row)


runoobdb=# select 60 & 13;
 ?column?
----------
       12
(1 row)


runoobdb=#  select  (~60);
 ?column?
----------
      -61
(1 row)


runoobdb=# select  (60 << 2);
 ?column?
----------
      240
(1 row)


runoobdb=# select  (60 >> 2);
 ?column?
----------
       15
(1 row)


runoobdb=#  select 60 # 13;
 ?column?
----------
       49
(1 row)
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PostgreSQL 运算符` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
