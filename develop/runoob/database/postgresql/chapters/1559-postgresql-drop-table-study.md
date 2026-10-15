# PostgreSQL：PostgreSQL 删除表格

- 来源：[PostgreSQL 删除表格](https://www.runoob.com/postgresql/postgresql-drop-table.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：学习笔记
- 章节序号：1559

## 本章内容

PostgreSQL 使用 DROP TABLE 语句来删除表格，包含表格数据、规则、触发器等，所以删除表格要慎重，删除后所有信息就消失了。


### 语法

DROP TABLE 语法格式如下：

```text
DROP TABLE table_name;
```


### 实例

上一章节中我们创建了 COMPANY 和 DEPARTMENT 两个表格，我们可以先使用 \d 命令来查看表格是否创建成功：

```text
runoobdb=# \d
           List of relations
 Schema |    Name    | Type  |  Owner
--------+------------+-------+----------
 public | company    | table | postgres
 public | department | table | postgres
(2 rows)
```

从以上结果可以看出，我们表格已经创建成功，接下来我们删除这两个表格：

```text
runoobdb=# drop table department, company;
DROP TABLE
```

再使用 \d 命令来查看就找不到表格了：

```text
testdb=# \d
Did not find any relations.
```


## 复习重点

- 能说明 `PostgreSQL 删除表格` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
