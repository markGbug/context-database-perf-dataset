# MySQL：MySQL 正则表达式

- 来源：[MySQL 正则表达式](https://www.runoob.com/mysql/mysql-regexp.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：学习笔记
- 章节序号：1528

## 本章内容

在前面的章节我们已经了解到 MySQL 可以通过 LIKE ...% 来进行模糊匹配。

MySQL 同样也支持其他正则表达式的匹配， MySQL 中使用 REGEXP 和 RLIKE操作符来进行正则表达式匹配。

如果您了解 PHP 或 Perl，那么操作起来就非常简单，因为 MySQL 的正则表达式匹配与这些脚本的类似。

下表中的正则模式可应用于 REGEXP 操作符中。


### 正则表达式匹配的字符类

- .：匹配任意单个字符。
- ^：匹配字符串的开始。
- $：匹配字符串的结束。
- *：匹配零个或多个前面的元素。
- +：匹配一个或多个前面的元素。
- ?：匹配零个或一个前面的元素。
- [abc]：匹配字符集中的任意一个字符。
- [^abc]：匹配除了字符集中的任意一个字符以外的字符。
- [a-z]：匹配范围内的任意一个小写字母。
- [0-9]：匹配一个数字字符。
- \w：匹配一个字母数字字符（包括下划线）。
- \s：匹配一个空白字符。


## 使用 REGEXP 进行模式匹配

REGEXP 是用于进行正则表达式匹配的运算符。

REGEXP 用于检查一个字符串是否匹配指定的正则表达式模式，以下是 REGEXP 运算符的基本语法：

```text
SELECT column1, column2, ...
FROM table_name
WHERE column_name REGEXP 'pattern';
```

参数说明：

- column1, column2, ... 是你要选择的列的名称，如果使用 * 表示选择所有列。
- table_name 是你要从中查询数据的表的名称。
- column_name 是你要进行正则表达式匹配的列的名称。
- 'pattern' 是一个正则表达式模式。

查找 name 字段中以 'st' 为开头的所有数据：

```text
mysql> SELECT name FROM person_tbl WHERE name REGEXP '^st';
```

查找 name 字段中以 'ok' 为结尾的所有数据：

```text
mysql> SELECT name FROM person_tbl WHERE name REGEXP 'ok$';
```

查找 name 字段中包含 'mar' 字符串的所有数据：

```text
mysql> SELECT name FROM person_tbl WHERE name REGEXP 'mar';
```

查找 name 字段中以元音字符开头或以 'ok' 字符串结尾的所有数据：

```text
mysql> SELECT name FROM person_tbl WHERE name REGEXP '^[aeiou]|ok$';
```

选择订单表中描述中包含 "item" 后跟一个或多个数字的记录。

```text
SELECT * FROM orders WHERE order_description REGEXP 'item[0-9]+';
```

使用 BINARY 关键字，使得匹配区分大小写：

```text
SELECT * FROM products WHERE product_name REGEXP BINARY 'apple';
```

使用 OR 进行多个匹配条件，以下将选择姓氏为 "Smith" 或 "Johnson" 的员工记录：

```text
SELECT * FROM employees WHERE last_name REGEXP 'Smith|Johnson';
```


### 使用 RLIKE 进行模式匹配

RLIKE 是 MySQL 中用于进行正则表达式匹配的运算符，与 REGEXP 是一样的，RLIKE 和 REGEXP 可以互换使用，没有区别。

以下是使用 RLIKE 进行正则表达式匹配的基本语法：

```text
SELECT column1, column2, ...
FROM table_name
WHERE column_name RLIKE 'pattern';
```

参数说明：

- column1, column2, ... 是你要选择的列的名称，如果使用 * 表示选择所有列。
- table_name 是你要从中查询数据的表的名称。
- column_name 是你要进行正则表达式匹配的列的名称。
- 'pattern' 是一个正则表达式模式。

```text
SELECT * FROM products WHERE product_name RLIKE '^[0-9]';
```

以上 SQL 语句选择产品名称以数字开头的所有产品。


## 复习重点

- 能说明 `MySQL 正则表达式` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
