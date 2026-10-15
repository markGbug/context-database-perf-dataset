# PostgreSQL：PostgreSQL 选择数据库

- 来源：[PostgreSQL 选择数据库](https://www.runoob.com/postgresql/postgresql-select-database.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：练习笔记
- 章节序号：1556

## 本章内容

上一章节我们讲了如何创建数据库，接下来我们来讨论如何去选择我们创建的数据库。


### 数据库的命令窗口

PostgreSQL 命令窗口中，我们可以命令提示符后面输入 SQL 语句：

```text
postgres=#
```

使用 \l 用于查看已经存在的数据库：

```text
postgres=# \l
                             List of databases
   Name    |  Owner   | Encoding | Collate | Ctype |   Access privileges
-----------+----------+----------+---------+-------+-----------------------
 postgres  | postgres | UTF8     | C       | C     |
 runoobdb  | postgres | UTF8     | C       | C     |
 template0 | postgres | UTF8     | C       | C     | =c/postgres          +
           |          |          |         |       | postgres=CTc/postgres
 template1 | postgres | UTF8     | C       | C     | =c/postgres          +
           |          |          |         |       | postgres=CTc/postgres
(4 rows)
```

接下来我们可以使用 \c + 数据库名 来进入数据库：

```text
postgres=# \c runoobdb
You are now connected to database "runoobdb" as user "postgres".
runoobdb=#
```


### 系统命令行窗口

在系统的命令行查看，我们可以在连接数据库后面添加数据库名来选择数据库：

```text
$ psql -h localhost -p 5432 -U postgres runoobdb
Password for user postgres: ****
psql (11.3)
Type "help" for help.
You are now connected to database "runoobdb" as user "postgres".
runoobdb=#
```


### pgAdmin 工具

pgAdmin 工具更简单了，直接点击数据库选择就好了，还可以查看一些数据库额外的信息：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PostgreSQL 选择数据库` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
