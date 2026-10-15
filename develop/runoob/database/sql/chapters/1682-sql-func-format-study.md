# SQL：SQL FORMAT() 函数

- 来源：[SQL FORMAT()](https://www.runoob.com/sql/sql-func-format.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：学习笔记
- 章节序号：1682

## 本章内容

## FORMAT() 函数

FORMAT() 函数用于对字段的显示进行格式化。


### SQL FORMAT() 语法


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


## SQL FORMAT() 实例

下面的 SQL 语句从 "Websites" 表中选取 name, url 以及格式化为 YYYY-MM-DD 的日期：


## 实例

执行以上 SQL 输出结果如下：


## 复习重点

- 能说明 `SQL FORMAT()` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
