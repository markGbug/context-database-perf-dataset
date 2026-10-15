# PHP：PHP MySQL 简介

- 来源：[PHP MySQL 简介](https://www.runoob.com/php/php-mysql-intro.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1082

## 本章内容

通过 PHP，您可以连接和操作数据库。

MySQL 是跟 PHP 配套使用的最流行的开源数据库系统。

如果想学习更多 MySQL 知识可以查看本站 MySQL 教程。


## MySQL 是什么？

- MySQL 是一种在 Web 上使用的数据库系统。
- MySQL 是一种在服务器上运行的数据库系统。
- MySQL 不管在小型还是大型应用程序中，都是理想的选择。
- MySQL 是非常快速，可靠，且易于使用的。
- MySQL 支持标准的 SQL。
- MySQL 在一些平台上编译。
- MySQL 是免费下载使用的。
- MySQL 是由 Oracle 公司开发、发布和支持的。
- MySQL 是以公司创始人 Monty Widenius's daughter: My 命名的。

MySQL 中的数据存储在表中。表格是一个相关数据的集合，它包含了列和行。

在分类存储信息时，数据库非常有用。一个公司的数据库可能拥有以下表：

- Employees
- Products
- Customers
- Orders


## PHP + MySQL

- PHP 与 MySQL 结合是跨平台的。（您可以在 Windows 上开发，在 Unix 平台上应用。）


## 查询

查询是一种询问或请求。

通过 MySQL，我们可以向数据库查询具体的信息，并得到返回的记录集。

请看下面的查询（使用标准 SQL）：

```text
mysql> set names utf8;
mysql> SELECT name FROM websites;
+---------------+
| name          |
+---------------+
| Google        |
| 淘宝        |
| 菜鸟教程  |
| 微博        |
| Facebook      |
| stackoverflow |
+---------------+
6 rows in set (0.00 sec)
```

语句 set names utf8;用于设定数据库编码，让中文可以正常显示。

上面的查询选取了 "websites" 表中 "name" 列的所有数据。

如需学习更多关于 SQL 的知识，请访问我们的 SQL 教程。


## 下载 MySQL 数据库

如果您的 PHP 服务器没有 MySQL 数据库，可以在此免费下载 MySQL： http://www.mysql.com。


## 关于 MySQL 数据库的事实

关于 MySQL 的一点很棒的特性是，可以对它进行缩减，来支持嵌入的数据库应用程序。也许正因为如此，许多人认为 MySQL 仅仅能处理中小型的系统。

事实上，对于那些支持巨大数据和访问量的网站（比如 Friendster、Yahoo、Google），MySQL 是事实上的标准数据库。

这个地址提供了使用 MySQL 的公司的概览： http://www.mysql.com/customers/。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP MySQL 简介` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
