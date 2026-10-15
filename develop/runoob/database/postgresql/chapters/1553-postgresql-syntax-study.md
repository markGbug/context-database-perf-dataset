# PostgreSQL：PostgreSQL 语法

- 来源：[PostgreSQL 语法](https://www.runoob.com/postgresql/postgresql-syntax.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：学习笔记
- 章节序号：1553

## 本章内容

默认情况下 PostgreSQL 安装完成后，自带了一个命令行工具 SQL Shell(psql)。

Linux 系统可以直接切换到 postgres 用户来开启命令行工具：

```text
#  sudo -i -u postgres
```

Windows 系统一般在它的安装目录下：

Program Files → PostgreSQL 11.3 → SQL Shell(psql)

Mac OS 我们直接搜索就可以了找到：

进入命令行工具，我们可以使用 \help 来查看各个命令的语法 ：

```html
postgres-# \help <command_name>
```

例如，我们查看下 select 语句的语法：

```text
postgres=# \help SELECT
Command:     SELECT
Description: retrieve rows from a table or view
Syntax:
[ WITH [ RECURSIVE ] with_query [, ...] ]
SELECT [ ALL | DISTINCT [ ON ( expression [, ...] ) ] ]
    [ * | expression [ [ AS ] output_name ] [, ...] ]
    [ FROM from_item [, ...] ]
    [ WHERE condition ]
    [ GROUP BY grouping_element [, ...] ]
    [ HAVING condition [, ...] ]
    [ WINDOW window_name AS ( window_definition ) [, ...] ]
    [ { UNION | INTERSECT | EXCEPT } [ ALL | DISTINCT ] select ]
    [ ORDER BY expression [ ASC | DESC | USING operator ] [ NULLS { FIRST | LAST } ] [, ...] ]
    [ LIMIT { count | ALL } ]
    [ OFFSET start [ ROW | ROWS ] ]
    [ FETCH { FIRST | NEXT } [ count ] { ROW | ROWS } ONLY ]
    [ FOR { UPDATE | NO KEY UPDATE | SHARE | KEY SHARE } [ OF table_name [, ...] ] [ NOWAIT | SKIP LOCKED ] [...] ]

from_item 可以是以下选项之一：

    [ ONLY ] table_name [ * ] [ [ AS ] alias [ ( column_alias [, ...] ) ] ]
```


## SQL 语句

一个 SQL 语句通常包含了关键字、标识符（字段）、常量、特殊符号等，下面是一个简单的 SQL 语句：

```text
SELECT id, name FROM runoob
```


## PostgreSQL 命令


### ABORT

ABORT 用于退出当前事务。

```text
ABORT [ WORK | TRANSACTION ]
```


### ALTER AGGREGATE

修改一个聚集函数的定义 。

```text
ALTER AGGREGATE _name_ ( _argtype_ [ , ... ] ) RENAME TO _new_name_
ALTER AGGREGATE _name_ ( _argtype_ [ , ... ] ) OWNER TO _new_owner_
ALTER AGGREGATE _name_ ( _argtype_ [ , ... ] ) SET SCHEMA _new_schema_
```


### ALTER COLLATION

修改一个排序规则定义 。

```text
ALTER COLLATION _name_ RENAME TO _new_name_
ALTER COLLATION _name_ OWNER TO _new_owner_
ALTER COLLATION _name_ SET SCHEMA _new_schema_
```


### ALTER CONVERSION

修改一个编码转换的定义。

```text
ALTER CONVERSION name RENAME TO new_name
ALTER CONVERSION name OWNER TO new_owner
```


### ALTER DATABASE

修改一个数据库。

```text
ALTER DATABASE name SET parameter { TO | = } { value | DEFAULT }
ALTER DATABASE name RESET parameter
ALTER DATABASE name RENAME TO new_name
ALTER DATABASE name OWNER TO new_owner
```


### ALTER DEFAULT PRIVILEGES

定义默认的访问权限。

```text
ALTER DEFAULT PRIVILEGES
    [ FOR { ROLE | USER } target_role [, ...] ]
    [ IN SCHEMA schema_name [, ...] ]
    abbreviated_grant_or_revoke

where abbreviated_grant_or_revoke is one of:

GRANT { { SELECT | INSERT | UPDATE | DELETE | TRUNCATE | REFERENCES | TRIGGER }
    [, ...] | ALL [ PRIVILEGES ] }
    ON TABLES
    TO { [ GROUP ] role_name | PUBLIC } [, ...] [ WITH GRANT OPTION ]
...
```


### ALTER DOMAIN

修改一个域的定义。

```text
ALTER DOMAIN name { SET DEFAULT expression | DROP DEFAULT }
ALTER DOMAIN name { SET | DROP } NOT NULL
ALTER DOMAIN name ADD domain_constraint
ALTER DOMAIN name DROP CONSTRAINT constraint_name [ RESTRICT | CASCADE ]
ALTER DOMAIN name OWNER TO new_owner
```


### ALTER FUNCTION

修改一个函数的定义。

```text
ALTER FUNCTION name ( [ type [, ...] ] ) RENAME TO new_name
ALTER FUNCTION name ( [ type [, ...] ] ) OWNER TO new_owner
```


### ALTER GROUP

修改一个用户组。

```text
ALTER GROUP groupname ADD USER username [, ... ]
ALTER GROUP groupname DROP USER username [, ... ]
ALTER GROUP groupname RENAME TO new_name
```


### ALTER INDEX

修改一个索引的定义。

```text
ALTER INDEX name OWNER TO new_owner
ALTER INDEX name SET TABLESPACE indexspace_name
ALTER INDEX name RENAME TO new_name
```


### ALTER LANGUAGE

修改一个过程语言的定义。

```text
ALTER LANGUAGE name RENAME TO new_name
```


### ALTER OPERATOR

改变一个操作符的定义。

```text
ALTER OPERATOR name ( { lefttype | NONE }, { righttype | NONE } )
OWNER TO new_owner
```


### ALTER OPERATOR CLASS

修改一个操作符表的定义。

```text
ALTER OPERATOR CLASS name USING index_method RENAME TO new_name
ALTER OPERATOR CLASS name USING index_method OWNER TO new_owner
```


### ALTER SCHEMA

修改一个模式的定义。

```text
ALTER SCHEMA name RENAME TO new_name
ALTER SCHEMA name OWNER TO new_owner
```


### ALTER SEQUENCE

修改一个序列生成器的定义。

```text
ALTER SEQUENCE name [ INCREMENT [ BY ] increment ]
[ MINVALUE minvalue | NO MINVALUE ]
[ MAXVALUE maxvalue | NO MAXVALUE ]
[ RESTART [ WITH ] start ] [ CACHE cache ] [ [ NO ] CYCLE ]
```


### ALTER TABLE

修改表的定义。

```text
ALTER TABLE [ ONLY ] name [ * ]
action [, ... ]
ALTER TABLE [ ONLY ] name [ * ]
RENAME [ COLUMN ] column TO new_column
ALTER TABLE name
RENAME TO new_name
```

其中 action 可以是以选项之一：

```java
ADD [ COLUMN ] column_type [ column_constraint [ ... ] ]
DROP [ COLUMN ] column [ RESTRICT | CASCADE ]
ALTER [ COLUMN ] column TYPE type [ USING expression ]
ALTER [ COLUMN ] column SET DEFAULT expression
ALTER [ COLUMN ] column DROP DEFAULT
ALTER [ COLUMN ] column { SET | DROP } NOT NULL
ALTER [ COLUMN ] column SET STATISTICS integer
ALTER [ COLUMN ] column SET STORAGE { PLAIN | EXTERNAL | EXTENDED | MAIN }
ADD table_constraint
DROP CONSTRAINT constraint_name [ RESTRICT | CASCADE ]
CLUSTER ON index_name
SET WITHOUT CLUSTER
SET WITHOUT OIDS
OWNER TO new_owner
SET TABLESPACE tablespace_name
```


### ALTER TABLESPACE

修改一个表空间的定义。

```text
ALTER TABLESPACE name RENAME TO new_name
ALTER TABLESPACE name OWNER TO new_owner
```


### ALTER TRIGGER

修改改变一个触发器的定义 。

```text
ALTER TRIGGER name ON table RENAME TO new_name
```


### ALTER TYPE

修改一个类型的定义 。

```text
ALTER TYPE name OWNER TO new_owner
```


### ALTER USER

修改数据库用户帐号 。

```text
ALTER USER name [ [ WITH ] option [ ... ] ]
ALTER USER name RENAME TO new_name
ALTER USER name SET parameter { TO | = } { value | DEFAULT }
ALTER USER name RESET parameter
```

Where option can be −

```text
[ ENCRYPTED | UNENCRYPTED ] PASSWORD 'password'
| CREATEDB | NOCREATEDB
| CREATEUSER | NOCREATEUSER
| VALID UNTIL 'abstime'
```


### ANALYZE

收集与数据库有关的统计。

```text
ANALYZE [ VERBOSE ] [ table [ (column [, ...] ) ] ]
```


### BEGIN

开始一个事务块。

```text
BEGIN [ WORK | TRANSACTION ] [ transaction_mode [, ...] ]
```

transaction_mode 可以是以下选项之一：

```text
ISOLATION LEVEL {
   SERIALIZABLE | REPEATABLE READ | READ COMMITTED
   | READ UNCOMMITTED
}
READ WRITE | READ ONLY
```


## 后续章节

- CHECKPOINT
- CLOSE
- CLUSTER
- COMMENT
- COMMIT
- COPY
- CREATE AGGREGATE
- CREATE CAST
- CREATE CONSTRAINT TRIGGER
- CREATE CONVERSION
- CREATE DATABASE
- CREATE DOMAIN
- CREATE FUNCTION
- CREATE GROUP
- CREATE INDEX
- CREATE LANGUAGE

## 复习重点

- 能说明 `PostgreSQL 语法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
