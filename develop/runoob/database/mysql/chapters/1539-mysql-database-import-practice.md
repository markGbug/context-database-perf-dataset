# MySQL：MySQL 导入数据

- 来源：[MySQL 导入数据](https://www.runoob.com/mysql/mysql-database-import.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：练习笔记
- 章节序号：1539

## 本章内容

本章节我们为大家介绍几种简单的 MySQL 导入数据命令。


## 1、mysql 命令导入

使用 mysql 命令导入语法格式为：

```text
mysql -u your_username -p -h your_host -P your_port -D your_database
```

your_username、your_host、your_port、your_database 分别为你的 MySQL 用户名、主机、端口和数据库。

实例：

```text
# mysql -uroot -p123456 < runoob.sql
```

以上命令将将备份的整个数据库 runoob.sql 导入。

执行上述命令后，系统将要求输入 MySQL 用户的密码。输入密码并按Enter键。

这样，MySQL 将执行 SQL 文件中的语句，将数据导入到指定的数据库中。

请注意，如果 SQL 文件包含创建数据库的语句，确保在执行导入之前数据库已经存在。如果文件包含创建表的语句，确保表不存在或者是空的，以免导入数据时发生冲突。


## 2、source 命令导入

source 命令导入数据库需要先登录到数库终端：

```text
mysql> create database abc;      # 创建数据库
mysql> use abc;                  # 使用已创建的数据库
mysql> set names utf8;           # 设置编码
mysql> source /home/abc/abc.sql  # 导入备份数据库
```

使用 source 命令的好处是，你可以在 MySQL 命令行中直接执行，而无需退出 MySQL 并使用其他命令。


## 3、使用 LOAD DATA 导入数据


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MySQL 导入数据` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
