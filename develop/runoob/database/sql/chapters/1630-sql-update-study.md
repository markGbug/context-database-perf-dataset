# SQL：SQL UPDATE 语句

- 来源：[SQL UPDATE](https://www.runoob.com/sql/sql-update.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：学习笔记
- 章节序号：1630

## 本章内容

UPDATE 语句用于更新表中的记录。


## SQL UPDATE 语句

UPDATE 语句用于更新表中已存在的记录。


### SQL UPDATE 语法

```text
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

参数说明：

- table_name：要修改的表名称。
- column1, column2, ...：要修改的字段名称，可以为多个字段。
- value1, value2, ...：要修改的值，可以为多个值。
- condition：修改条件，用于指定哪些数据要修改。


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


## SQL UPDATE 实例

假设我们要把 "菜鸟教程" 的 alexa 排名更新为 5000，country 改为 USA。

我们使用下面的 SQL 语句：


## 实例

```text
UPDATE Websites
SET alexa='5000', country='USA'
WHERE name='菜鸟教程';
```

执行以上 SQL，再读取 "Websites" 表，数据如下所示：


## Update 警告！

在更新记录时要格外小心！在上面的实例中，如果我们省略了 WHERE 子句，如下所示：

```text
UPDATE Websites
SET alexa='5000', country='USA'
```

执行以上代码会将 Websites 表中所有数据的 alexa 改为 5000，country 改为 USA。

执行没有 WHERE 子句的 UPDATE 要慎重，再慎重。


## 复习重点

- 能说明 `SQL UPDATE` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
