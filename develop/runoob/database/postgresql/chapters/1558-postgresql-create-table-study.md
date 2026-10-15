# PostgreSQL：PostgreSQL 创建表格

- 来源：[PostgreSQL 创建表格](https://www.runoob.com/postgresql/postgresql-create-table.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：学习笔记
- 章节序号：1558

## 本章内容

PostgreSQL 使用 CREATE TABLE 语句来创建数据库表格。


### 语法

CREATE TABLE 语法格式如下：

```text
CREATE TABLE table_name(
   column1 datatype,
   column2 datatype,
   column3 datatype,
   .....
   columnN datatype,
   PRIMARY KEY( 一个或多个列 )
);
```

CREATE TABLE 是一个关键词，用于告诉数据库系统将创建一个数据表。

表名字必需在同一模式中的其它表、 序列、索引、视图或外部表名字中唯一。

CREATE TABLE 在当前数据库创建一个新的空白表，该表将由发出此命令的用户所拥有。

表格中的每个字段都会定义数据类型，如下：


### 实例

以下创建了一个表，表名为 COMPANY 表格，主键为 ID，NOT NULL 表示字段不允许包含 NULL 值：

```text
CREATE TABLE COMPANY(
   ID INT PRIMARY KEY     NOT NULL,
   NAME           TEXT    NOT NULL,
   AGE            INT     NOT NULL,
   ADDRESS        CHAR(50),
   SALARY         REAL
);
```

接下来我们再创建一个表格，在后面章节会用到：

```text
CREATE TABLE DEPARTMENT(
   ID INT PRIMARY KEY      NOT NULL,
   DEPT           CHAR(50) NOT NULL,
   EMP_ID         INT      NOT NULL
);
```

我们可以使用 \d 命令来查看表格是否创建成功：

```text
runoobdb=# \d
           List of relations
 Schema |    Name    | Type  |  Owner
--------+------------+-------+----------
 public | company    | table | postgres
 public | department | table | postgres
(2 rows)
```

\d tablename 查看表格信息：

```text
runoobdb=# \d company
                  Table "public.company"
 Column  |     Type      | Collation | Nullable | Default
---------+---------------+-----------+----------+---------
 id      | integer       |           | not null |
 name    | text          |           | not null |
 age     | integer       |           | not null |
 address | character(50) |           |          |
 salary  | real          |           |          |
Indexes:
    "company_pkey" PRIMARY KEY, btree (id)
```


## 复习重点

- 能说明 `PostgreSQL 创建表格` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
