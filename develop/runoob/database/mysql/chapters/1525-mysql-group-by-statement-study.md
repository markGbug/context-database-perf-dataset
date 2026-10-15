# MySQL：MySQL GROUP BY 语句

- 来源：[MySQL 分组](https://www.runoob.com/mysql/mysql-group-by-statement.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：学习笔记
- 章节序号：1525

## 本章内容

GROUP BY 语句根据一个或多个列对结果集进行分组。

在分组的列上我们可以使用 COUNT, SUM, AVG,等函数。

GROUP BY 语句是 SQL 查询中用于汇总和分析数据的重要工具，尤其在处理大量数据时，它能够提供有用的汇总信息。


### GROUP BY 语法

```text
SELECT column1, aggregate_function(column2)
FROM table_name
WHERE condition
GROUP BY column1;
```

- column1：指定分组的列。
- aggregate_function(column2)：对分组后的每个组执行的聚合函数。
- table_name：要查询的表名。
- condition：可选，用于筛选结果的条件。

假设有一个名为 orders 的表，包含以下列：order_id、customer_id、order_date 和 order_amount。

我们想要按照 customer_id 进行分组，并计算每个客户的订单总金额，SQL 语句如下：


## 实例

以上实例中，我们使用 GROUP BY customer_id 将结果按 customer_id 列分组，然后使用 SUM(order_amount) 计算每个组中 order_amount 列的总和。

AS total_amount 是为了给计算结果取一个别名，使查询结果更易读。

注意事项：

- GROUP BY 子句通常与聚合函数一起使用，因为分组后需要对每个组进行聚合操作。
- SELECT 子句中的列通常要么是分组列，要么是聚合函数的参数。
- 可以使用多个列进行分组，只需在 GROUP BY 子句中用逗号分隔列名即可。


## 实例


## 实例演示

本章节实例使用到了以下表结构及数据，使用前我们可以先将以下数据导入数据库中。


## 实例

导入成功后，执行以下 SQL 语句：

```text
mysql> set names utf8;
mysql> SELECT * FROM employee_tbl;
+----+--------+---------------------+--------+
| id | name   | date                | signin |
+----+--------+---------------------+--------+
|  1 | 小明 | 2016-04-22 15:25:33 |      1 |
|  2 | 小王 | 2016-04-20 15:25:47 |      3 |
|  3 | 小丽 | 2016-04-19 15:26:02 |      2 |
|  4 | 小王 | 2016-04-07 15:26:14 |      4 |
|  5 | 小明 | 2016-04-11 15:26:40 |      4 |
|  6 | 小明 | 2016-04-04 15:26:54 |      2 |
+----+--------+---------------------+--------+
6 rows in set (0.00 sec)
```

接下来我们使用 GROUP BY 语句 将数据表按名字进行分组，并统计每个人有多少条记录：

```text
mysql> SELECT name, COUNT(*) FROM   employee_tbl GROUP BY name;
+--------+----------+
| name   | COUNT(*) |
+--------+----------+
| 小丽 |        1 |
| 小明 |        3 |
| 小王 |        2 |
+--------+----------+
3 rows in set (0.01 sec)
```


### 使用 WITH ROLLUP

WITH ROLLUP 可以实现在分组统计数据基础上再进行相同的统计（SUM,AVG,COUNT…）。

例如我们将以上的数据表按名字进行分组，再统计每个人登录的次数：

```text
mysql> SELECT name, SUM(signin) as signin_count FROM  employee_tbl GROUP BY name WITH ROLLUP;
+--------+--------------+
| name   | signin_count |
+--------+--------------+
| 小丽 |            2 |
| 小明 |            7 |
| 小王 |            7 |
| NULL   |           16 |
+--------+--------------+
4 rows in set (0.00 sec)
```

其中记录 NULL 表示所有人的登录次数。

我们可以使用 coalesce 来设置一个可以取代 NUll 的名称，coalesce 语法：

```text
select coalesce(a,b,c);
```

参数说明：如果 a==null，则选择 b；如果 b==null,则选择 c；如果 a!=null,则选择 a；如果 a b c 都为 null ，则返回为 null（没意义）。

以下实例中如果名字为空我们使用总数代替：

```text
mysql> SELECT coalesce(name, '总数'), SUM(signin) as signin_count FROM  employee_tbl GROUP BY name WITH ROLLUP;
+--------------------------+--------------+
| coalesce(name, '总数') | signin_count |
+--------------------------+--------------+
| 小丽                   |            2 |
| 小明                   |            7 |
| 小王                   |            7 |
| 总数                   |           16 |
+--------------------------+--------------+
4 rows in set (0.01 sec)
```


## 复习重点

- 能说明 `MySQL 分组` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
