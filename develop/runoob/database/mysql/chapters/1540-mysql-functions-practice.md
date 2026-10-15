# MySQL：MySQL 函数

- 来源：[MySQL 函数](https://www.runoob.com/mysql/mysql-functions.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：练习笔记
- 章节序号：1540

## 本章内容

MySQL 有很多内置的函数，以下列出了这些函数的说明。


## MySQL 字符串函数

返回 CustomerName 字段第一个字母的 ASCII 码：

```text
SELECT ASCII(CustomerName) AS NumCodeOfFirstChar
FROM Customers;
```

返回字符串 RUNOOB 的字符数

```text
SELECT CHAR_LENGTH("RUNOOB") AS LengthOfString;
```

返回字符串 RUNOOB 的字符数

```text
SELECT CHARACTER_LENGTH("RUNOOB") AS LengthOfString;
```

合并多个字符串

```text
SELECT CONCAT("SQL ", "Runoob ", "Gooogle ", "Facebook") AS ConcatenatedString;
```

合并多个字符串，并添加分隔符：

```text
SELECT CONCAT_WS("-", "SQL", "Tutorial", "is", "fun!")AS ConcatenatedString;
```

返回字符串 c 在列表值中的位置：

```text
SELECT FIELD("c", "a", "b", "c", "d", "e");
```

返回字符串 c 在指定字符串中的位置：

```text
SELECT FIND_IN_SET("c", "a,b,c,d,e");
```

格式化数字 "#,###.##" 形式：

```text
SELECT FORMAT(250500.5634, 2);     -- 输出 250,500.56
```

从字符串第一个位置开始的 6 个字符替换为 runoob：

```text
SELECT INSERT("google.com", 1, 6, "runoob");  -- 输出：runoob.com
```

获取 b 在字符串 abc 中的位置：

```text
SELECT LOCATE('st','myteststring');  -- 5
```

返回字符串 abc 中 b 的位置：

```text
SELECT LOCATE('b', 'abc') -- 2
```

字符串 RUNOOB 转换为小写：

```text
SELECT LCASE('RUNOOB') -- runoob
```

返回字符串 runoob 中的前两个字符：

```text
SELECT LEFT('runoob',2) -- ru
```

字符串 RUNOOB 转换为小写：

```text
SELECT LOWER('RUNOOB') -- runoob
```


## MySQL 数字函数

返回 -1 的绝对值：

```text
SELECT ABS(-1) -- 返回1
```

```text
SELECT ACOS(0.25);
```

```text
SELECT ASIN(0.25);
```

```text
SELECT ATAN(2.5);
```

```text
SELECT ATAN2(-0.8, 2);
```

返回 Products 表中Price 字段的平均值：

```text
SELECT AVG(Price) AS AveragePrice FROM Products;
```

```text
SELECT CEIL(1.5) -- 返回2
```

```text
SELECT CEILING(1.5); -- 返回2
```

```text
SELECT COS(2);
```

```text
SELECT COT(6);
```

返回 Products 表中 products 字段总共有多少条记录：

```text
SELECT COUNT(ProductID) AS NumberOfProducts FROM Products;
```

```text
SELECT DEGREES(3.1415926535898) -- 180
```

计算 10 除于 5：

```text
SELECT 10 DIV 5;  -- 2
```

计算 e 的三次方：

```text
SELECT EXP(3) -- 20.085536923188
```

小于或等于 1.5 的整数：

```text
SELECT FLOOR(1.5) -- 返回1
```

返回以下数字列表中的最大值：

```text
SELECT GREATEST(3, 12, 34, 8, 25); -- 34
```

返回以下字符串列表中的最大值：

```text
SELECT GREATEST("Google", "Runoob", "Apple");   -- Runoob
```

返回以下数字列表中的最小值：

```text
SELECT LEAST(3, 12, 34, 8, 25); -- 3
```

返回以下字符串列表中的最小值：


## MySQL 日期函数

```text
SELECT ADDDATE("2017-06-15", INTERVAL 10 DAY);
->2017-06-25
```

加 5 秒：

```text
SELECT ADDTIME('2011-11-11 11:11:11', 5);
->2011-11-11 11:11:16 (秒)
```

添加 2 小时, 10 分钟, 5 秒:

```text
SELECT ADDTIME("2020-06-15 09:34:21", "2:10:5");
-> 2020-06-15 11:44:26
```

```text
SELECT CURDATE();
-> 2018-09-19
```

```text
SELECT CURRENT_DATE();
-> 2018-09-19
```

```text
SELECT CURRENT_TIME();
-> 19:59:02
```

```text
SELECT CURRENT_TIMESTAMP()
-> 2018-09-19 20:57:43
```

```text
SELECT CURTIME();
-> 19:59:02
```

```text
SELECT DATE("2017-06-15");
-> 2017-06-15
```

```text
SELECT DATEDIFF('2001-01-01','2001-02-02')
-> -32
```

- MICROSECOND
- SECOND
- MINUTE
- HOUR
- DAY
- WEEK
- MONTH
- QUARTER
- YEAR
- SECOND_MICROSECOND
- MINUTE_MICROSECOND
- MINUTE_SECOND
- HOUR_MICROSECOND
- HOUR_SECOND
- HOUR_MINUTE
- DAY_MICROSECOND


## MySQL 高级函数

15 的 2 进制编码:

```text
SELECT BIN(15); -- 1111
```

```text
SELECT BINARY "RUNOOB";
-> RUNOOB
```

```text
CASE expression
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
   ...
    WHEN conditionN THEN resultN
    ELSE result
END
```

```text
SELECT CASE
　　WHEN 1 > 0
　　THEN '1 > 0'
　　WHEN 2 > 0
　　THEN '2 > 0'
　　ELSE '3 > 0'
　　END
->1 > 0
```

字符串日期转换为日期：

```text
SELECT CAST("2017-08-29" AS DATE);
-> 2017-08-29
```

```text
SELECT COALESCE(NULL, NULL, NULL, 'runoob.com', NULL, 'google.com');
-> runoob.com
```

```text
SELECT CONNECTION_ID();
-> 4292835
```

```text
SELECT CONV(15, 10, 2);
-> 1111
```

```text
SELECT CHARSET('ABC')
->utf-8

SELECT CHARSET(CONVERT('ABC' USING gbk))
->gbk
```

```text
SELECT CURRENT_USER();
-> guest@%
```

```text
SELECT DATABASE();
-> runoob
```

```text
SELECT IF(1 > 0,'正确','错误')
->正确
```

```text
SELECT IFNULL(null,'Hello Word')
->Hello Word
```

```text
SELECT ISNULL(NULL);
->1
```

```text
SELECT LAST_INSERT_ID();
->6
```

```text
SELECT NULLIF(25, 25);
->
```

```text
SELECT SESSION_USER();
-> guest@%
```

```text
SELECT SYSTEM_USER();
-> guest@%
```

```text
SELECT USER();
-> guest@%
```

```text
SELECT VERSION()
-> 5.6.34
```

以下是 MySQL 8.0 版本新增的一些常用函数：

```text
SELECT JSON_OBJECT('key1', 'value1', 'key2', 'value2')
```

```text
SELECT JSON_ARRAY(1, 2, 'three')
```

```text
SELECT JSON_EXTRACT('{"name": "John", "age": 30}', '$.name')
```

```text
SELECT JSON_CONTAINS('{"name": "John", "age": 30}', 'John', '$.name')
```

```text
SELECT ROW_NUMBER() OVER(ORDER BY id) AS row_number, name FROM users
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MySQL 函数` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
