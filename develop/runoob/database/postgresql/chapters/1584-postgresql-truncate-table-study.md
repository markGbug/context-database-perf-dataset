# PostgreSQL：PostgreSQL TRUNCATE TABLE

- 来源：[PostgreSQL TRUNCATE TABLE](https://www.runoob.com/postgresql/postgresql-truncate-table.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：学习笔记
- 章节序号：1584

## 本章内容

PostgreSQL 中 TRUNCATE TABLE 用于删除表的数据，但不删除表结构。

也可以用 DROP TABLE 删除表，但是这个命令会连表的结构一起删除，如果想插入数据，需要重新建立这张表。

PostgreSQL VACUUM 操作用于释放、再利用更新/删除行所占据的磁盘空间。


### 语法

TRUNCATE TABLE 基础语法如下：

```text
TRUNCATE TABLE  table_name;
```


### 实例

创建 COMPANY 表（下载 COMPANY SQL 文件 ），数据内容如下：

```text
runoobdb# select * from COMPANY;
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

下面实例使用了 TRUNCATE TABLE 来清除 COMPANY 表：

```text
runoobdb=# TRUNCATE TABLE COMPANY;
```

得到结果如下：

```text
runoobdb=# SELECT * FROM CUSTOMERS;
 id | name | age | address | salary
----+------+-----+---------+--------
(0 rows)
```


## 复习重点

- 能说明 `PostgreSQL TRUNCATE TABLE` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
