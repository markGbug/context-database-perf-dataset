# SQL：SQL WHERE 子句

- 来源：[SQL WHERE](https://www.runoob.com/sql/sql-where.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：练习笔记
- 章节序号：1626

## 本章内容

WHERE 子句用于过滤记录。


## SQL WHERE 子句

WHERE 子句用于提取那些满足指定条件的记录。


### SQL WHERE 语法

```text
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

参数说明：

- column1, column2, ...：要选择的字段名称，可以为多个字段。如果不指定字段名称，则会选择所有字段。
- table_name：要查询的表名称。


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


## WHERE 子句实例

下面的 SQL 语句从 "Websites" 表中选取国家为 "CN" 的所有网站：


## 实例

```text
SELECT * FROM Websites WHERE country='CN';
```

执行输出结果：


## 文本字段 vs. 数值字段

SQL 使用单引号来环绕文本值（大部分数据库系统也接受双引号）。

在上个实例中 'CN' 文本字段使用了单引号。

如果是数值字段，请不要使用引号。


## 实例

```text
SELECT * FROM Websites WHERE id=1;
```

执行输出结果：


## WHERE 子句中的运算符

下面的运算符可以在 WHERE 子句中使用：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQL WHERE` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
