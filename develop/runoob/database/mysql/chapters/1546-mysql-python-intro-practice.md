# MySQL：MySQL Python 连接与使用

- 来源：[MySQL Python](https://www.runoob.com/mysql/mysql-python-intro.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：练习笔记
- 章节序号：1546

## 本章内容

MySQL 是最流行的开源关系型数据库之一，而 Python 是当今最受欢迎的编程语言之一。将 Python 与 MySQL 结合使用，可以让我们轻松地开发数据库驱动的应用程序。

本文将详细介绍如何使用 Python 连接和操作 MySQL 数据库，内容包含如下：

- 如何安装 MySQL Python 驱动
- 建立和关闭数据库连接
- 执行各种 SQL 查询
- 事务管理和错误处理
- 数据库操作的最佳实践


## 准备工作


### 安装必要的软件

在开始之前，请确保你已经安装了以下软件：

- Python (推荐 3.6 或更高版本)
- MySQL Server (社区版即可)
- MySQL Connector/Python (Python 的 MySQL 驱动)


### 安装 MySQL Connector/Python

可以通过 pip 安装 MySQL 官方提供的 Python 驱动：

```text
pip install mysql-connector-python
```

或者安装 PyMySQL (另一个流行的 MySQL Python 驱动):

```text
pip install pymysql
```


## 连接 MySQL 数据库


### 建立基本连接

以下是使用 mysql-connector-python 建立数据库连接的基本代码：


## 实例


### 连接参数说明

- host: MySQL 服务器地址 (本地为 "localhost")
- user: 数据库用户名
- password: 用户密码
- database: 要连接的数据库名称 (可选)


### 使用 PyMySQL 连接

如果你选择使用 PyMySQL，连接方式略有不同：


## 实例


## 执行 SQL 查询


### 创建游标对象

在执行 SQL 语句前，我们需要创建一个游标(cursor)对象：


## 实例


### 执行 SELECT 查询


## 实例


### 执行 INSERT, UPDATE, DELETE 操作


## 实例


### 使用参数化查询

为了防止 SQL 注入，应该始终使用参数化查询：


## 实例


## 事务管理


### 事务的基本概念

MySQL 事务是一组原子性的 SQL 查询，要么全部执行成功，要么全部不执行。


### 使用事务


## 实例


## 错误处理


### 捕获数据库错误


## 后续章节

- 实例
- 常见错误代码
- 关闭连接
- 正确关闭连接
- 实例
- 使用 with 语句
- 实例
- 最佳实践
- 连接池
- 实例
- ORM 框架

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MySQL Python` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
