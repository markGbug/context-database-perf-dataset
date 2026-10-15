# SQL：SQL LAST() 函数

- 来源：[SQL LAST()](https://www.runoob.com/sql/sql-func-last.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：学习笔记
- 章节序号：1669

## 本章内容

## LAST() 函数

LAST() 函数返回指定的列中最后一个记录的值。


### SQL LAST() 语法

注释：只有 MS Access 支持 LAST() 函数。


## SQL Server、MySQL 和 Oracle 中的 SQL LAST() 工作区


### SQL Server 语法


### 实例


### MySQL 语法


### 实例


### Oracle 语法


### 实例


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
|  6 | 百度         | https://www.baidu.com/    |     4 | CN      |
|  7 | stackoverflow | http://stackoverflow.com/ |     0 | IND     |
+----+---------------+---------------------------+-------+---------+
```


## SQL LAST() 实例

下面的 SQL 语句选取 "Websites" 表的 "name" 列中最后一个记录的值：


## 实例

执行以上 SQL 结果如下所示：


## 复习重点

- 能说明 `SQL LAST()` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
