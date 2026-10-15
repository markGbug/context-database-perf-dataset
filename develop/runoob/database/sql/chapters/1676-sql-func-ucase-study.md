# SQL：SQL UCASE() 函数

- 来源：[SQL UCASE()](https://www.runoob.com/sql/sql-func-ucase.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：学习笔记
- 章节序号：1676

## 本章内容

## UCASE() 函数

UCASE() 函数把字段的值转换为大写。


### SQL UCASE() 语法


### 用于 SQL Server 的语法


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
| 7  | stackoverflow | http://stackoverflow.com/ |   0 | IND     |
+----+---------------+---------------------------+-------+---------+
```


## SQL UCASE() 实例

下面的 SQL 语句从 "Websites" 表中选取 "name" 和 "url" 列，并把 "name" 列的值转换为大写：


## 实例

执行以上 SQL 输出结果如下：


## 复习重点

- 能说明 `SQL UCASE()` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
