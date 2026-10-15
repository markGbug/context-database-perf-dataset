# PostgreSQL：PostgreSQL 模式（SCHEMA）

- 来源：[PostgreSQL 模式](https://www.runoob.com/postgresql/postgresql-schema.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：学习笔记
- 章节序号：1560

## 本章内容

PostgreSQL 模式（SCHEMA）可以看着是一个表的集合。

一个模式可以包含视图、索引、数据类型、函数和操作符等。

相同的对象名称可以被用于不同的模式中而不会出现冲突，例如 schema1 和 myschema 都可以包含名为 mytable 的表。

使用模式的优势：

- 允许多个用户使用一个数据库并且不会互相干扰。
- 将数据库对象组织成逻辑组以便更容易管理。
- 第三方应用的对象可以放在独立的模式中，这样它们就不会与其他对象的名称发生冲突。


### 语法

我们可以使用 CREATE SCHEMA 语句来创建模式，语法格式如下：

```text
CREATE SCHEMA myschema (
...
);
```

上述语句将创建一个名为 myschema 的模式。

模式通常用于组织和隔离数据库对象，防止对象名称冲突。

创建表（Table）使用 CREATE TABLE 语句:

```text
CREATE TABLE myschema.mytable (
    column1 datatype1,
    column2 datatype2,
    ...
);
```

上述语句将在 myschema 模式下创建一个名为 mytable 的表，并定义了一系列的列及其数据类型。

请注意，上述的 datatype1, datatype2 等应该被替换为实际的数据类型，例如 integer, varchar(255), 等等。


### 实例

接下来我们连接到 runoobdb 来创建模式 myschema：

```text
runoobdb=# create schema myschema;
CREATE SCHEMA
```

输出结果 "CREATE SCHEMA" 就代表模式创建成功。

接下来我们再创建一个表格：

```text
runoobdb=# create table myschema.company(
   ID   INT              NOT NULL,
   NAME VARCHAR (20)     NOT NULL,
   AGE  INT              NOT NULL,
   ADDRESS  CHAR (25),
   SALARY   DECIMAL (18, 2),
   PRIMARY KEY (ID)
);
```

以上命令创建了一个空的表格，我们使用以下 SQL 来查看表格是否创建：

```text
runoobdb=# select * from myschema.company;
 id | name | age | address | salary
----+------+-----+---------+--------
(0 rows)
```


### 删除模式

删除一个为空的模式（其中的所有对象已经被删除）：

```text
DROP SCHEMA myschema;
```

删除一个模式以及其中包含的所有对象：

```text
DROP SCHEMA myschema CASCADE;
```


## 复习重点

- 能说明 `PostgreSQL 模式` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
