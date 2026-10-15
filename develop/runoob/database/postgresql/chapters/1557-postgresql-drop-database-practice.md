# PostgreSQL：PostgreSQL 删除数据库

- 来源：[PostgreSQL 删除数据库](https://www.runoob.com/postgresql/postgresql-drop-database.html)
- 分类：数据库
- 技术：PostgreSQL
- 笔记类型：练习笔记
- 章节序号：1557

## 本章内容

PostgreSQL 删除数据库可以用以下三种方式：

- 1、使用 DROP DATABASE SQL 语句来删除。
- 2、使用 dropdb 命令来删除。
- 3、使用 pgAdmin 工具。

注意：删除数据库要谨慎操作，一旦删除，所有信息都会消失。


### DROP DATABASE 删除数据库

DROP DATABASE 会删除数据库的系统目录项并且删除包含数据的文件目录。

DROP DATABASE 只能由超级管理员或数据库拥有者执行。

DROP DATABASE 命令需要在 PostgreSQL 命令窗口来执行，语法格式如下：

```text
DROP DATABASE [ IF EXISTS ] name
```

参数说明：

- IF EXISTS：如果数据库不存在则发出提示信息，而不是错误信息。
- name：要删除的数据库的名称。

例如，我们删除一个 runoobdb 的数据库：

```text
postgres=# DROP DATABASE runoobdb;
```


### dropdb 命令删除数据库

dropdb 是 DROP DATABASE 的包装器。

dropdb 用于删除 PostgreSQL 数据库。

dropdb 命令只能由超级管理员或数据库拥有者执行。

dropdb 命令语法格式如下：

```text
dropdb [connection-option...] [option...] dbname
```

参数说明：

dbname：要删除的数据库名。

options：参数可选项，可以是以下值：

-e

显示 dropdb 生成的命令并发送到数据库服务器。

-i

在做删除的工作之前发出一个验证提示。

-V

打印 dropdb 版本并退出。

--if-exists

如果数据库不存在则发出提示信息，而不是错误信息。

--help

显示有关 dropdb 命令的帮助信息。

-h host

指定运行服务器的主机名。

-p port

指定服务器监听的端口，或者 socket 文件。

-U username

连接数据库的用户名。

-w

连接时忽略输入密码。

-W

连接时强制要求输入密码。


### pgAdmin 工具删除据库

pgAdmin 工具提供了完整操作数据库的功能：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PostgreSQL 删除数据库` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
