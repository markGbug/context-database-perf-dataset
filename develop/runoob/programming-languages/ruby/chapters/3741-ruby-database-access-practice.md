# Ruby：Ruby 数据库访问 - DBI 教程

- 来源：[Ruby 数据库访问 - DBI 教程](https://www.runoob.com/ruby/ruby-database-access.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：练习笔记
- 章节序号：3741

## 本章内容

本章节将向您讲解如何使用 Ruby 访问数据库。Ruby DBI 模块为 Ruby 脚本提供了类似于 Perl DBI 模块的独立于数据库的接口。

DBI 即 Database independent interface，代表了 Ruby 独立于数据库的接口。DBI 在 Ruby 代码与底层数据库之间提供了一个抽象层，允许您简单地实现数据库切换。它定义了一系列方法、变量和规范，提供了一个独立于数据库的一致的数据库接口。

DBI 可与下列进行交互：

- ADO (ActiveX Data Objects)
- DB2
- Frontbase
- mSQL
- MySQL
- ODBC
- Oracle
- OCI8 (Oracle)
- PostgreSQL
- Proxy/Server
- SQLite
- SQLRelay


## DBI 应用架构

DBI 独立于任何在后台中可用的数据库。无论您使用的是 Oracle、MySQL、Informix，您都可以使用 DBI。下面的架构图清晰地说明了这点。

Ruby DBI 一般的架构使用两个层：

- 数据库接口（DBI）层。该层是独立于数据库，并提供了一系列公共访问方法，方法的使用不分数据库服务器类型。
- 数据库驱动（DBD）层。该层是依赖于数据库，不同的驱动提供了对不同的数据库引擎的访问。MySQL、PostgreSQL、InterBase、Oracle 等分别使用不同的驱动。每个驱动都负责解释来自 DBI 层的请求，并把这些请求映射为适用于给定类型的数据库服务器的请求。


## 安装

如果您想要编写 Ruby 脚本来访问 MySQL 数据库，您需要先安装 Ruby MySQL 模块。


### 安装 Mysql 开发包

```text
# Ubuntu
sudo apt-get install mysql-client
sudo apt-get install libmysqlclient15-dev

# Centos
yum install mysql-devel
```

Mac OS 系统需要修改 ~/.bash_profile 或 ~/.profile 文件，添加如下代码:

```text
MYSQL=/usr/local/mysql/bin
export PATH=$PATH:$MYSQL
export DYLD_LIBRARY_PATH=/usr/local/mysql/lib:$DYLD_LIBRARY_PATH
```

或者使用软连接：

```text
sudo ln -s /usr/local/mysql/lib/libmysqlclient.18.dylib /usr/lib/libmysqlclient.18.dylib
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ruby 数据库访问 - DBI 教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
