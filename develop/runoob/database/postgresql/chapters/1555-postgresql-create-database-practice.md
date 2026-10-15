# PostgreSQL：PostgreSQL 创建数据库

- 来源：[PostgreSQL 创建数据库](https://www.runoob.com/postgresql/postgresql-create-database.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：练习笔记
- 章节序号：1555

## 本章内容

PostgreSQL 创建数据库可以用以下三种方式：

- 1、使用 CREATE DATABASE SQL 语句来创建。
- 2、使用 createdb 命令来创建。
- 3、使用 pgAdmin 工具。


### CREATE DATABASE 创建数据库

CREATE DATABASE 命令需要在 PostgreSQL 命令窗口来执行，语法格式如下：

```text
CREATE DATABASE dbname;
```

例如，我们创建一个 runoobdb 的数据库：

```text
postgres=# CREATE DATABASE runoobdb;
```


### createdb 命令创建数据库

createdb 是一个 SQL 命令 CREATE DATABASE 的封装。

createdb 命令语法格式如下：

```text
createdb [option...] [dbname [description]]
```

参数说明：

dbname：要创建的数据库名。

description：关于新创建的数据库相关的说明。

options：参数可选项，可以是以下值：

-D tablespace

指定数据库默认表空间。

-e

将 createdb 生成的命令发送到服务端。

-E encoding

指定数据库的编码。

-l locale

指定数据库的语言环境。

-T template

指定创建此数据库的模板。

--help

显示 createdb 命令的帮助信息。

-h host

指定服务器的主机名。

-p port

指定服务器监听的端口，或者 socket 文件。

-U username

连接数据库的用户名。

-w

忽略输入密码。

-W


### pgAdmin 工具创建数据库

pgAdmin 工具提供了完整操作数据库的功能：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PostgreSQL 创建数据库` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
