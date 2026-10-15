# SQL：SQL DELETE 语句

- 来源：[SQL DELETE](https://www.runoob.com/sql/sql-delete.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：练习笔记
- 章节序号：1631

## 本章内容

DELETE 语句用于删除表中的记录。


## SQL DELETE 语句

DELETE 语句用于删除表中的行。


### SQL DELETE 语法

```text
DELETE FROM table_name
WHERE condition;
```

参数说明：

- table_name：要删除的表名称。
- condition：删除条件，用于指定哪些数据要删除。


## 演示数据库

在本教程中，我们将使用 RUNOOB 样本数据库。

下面是选自 "Websites" 表的数据：

```text
+----+--------------+---------------------------+-------+---------+
| id | name         | url                       | alexa | country |
+----+--------------+---------------------------+-------+---------+
| 1  | Google       | https://www.google.cm/    | 1     | USA     |
| 2  | 淘宝       | https://www.taobao.com/   | 13    | CN      |
| 3  | 菜鸟教程 | http://www.runoob.com/    | 4689  | CN      |
| 4  | 微博       | http://weibo.com/         | 20    | CN      |
| 5  | Facebook     | https://www.facebook.com/ | 3     | USA     |
+----+--------------+---------------------------+-------+---------+
```


## SQL DELETE 实例

假设我们要从 "Websites" 表中删除网站名为 "Facebook" 且国家为 USA 的网站。

我们使用下面的 SQL 语句：


## 实例

```text
DELETE FROM Websites
WHERE name='Facebook' AND country='USA';
```

执行以上 SQL，再读取 "Websites" 表，数据如下所示：


## 删除所有数据

您可以在不删除表的情况下，删除表中所有的行。这意味着表结构、属性、索引将保持不变：

注释：在删除记录时要格外小心！因为您不能重来！


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQL DELETE` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
