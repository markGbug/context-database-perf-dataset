# 知识点 81827：ASP.NET：WebForms 数据库连接 - 创建数据库连接

- 来源：[WebForms 数据库连接](https://www.runoob.com/aspnet/aspnet-dbconnection.html)
- 来源章节：[1977-aspnet-dbconnection-practice.md](../chapters/1977-aspnet-dbconnection-practice.md)
- 分类：.NET
- 技术：ASP.NET
- 所在小节：创建数据库连接
- 知识类型：解释
- 原章节序号：1977

## 原文片段

首先，导入 "System.Data.OleDb" 命名空间。我们需要这个命名空间来操作 Microsoft Access 和其他 OLE DB 数据库提供商。我们将在 Page_Load 子例程中创建这个数据库的连接。我们创建一个 dbconn 变量，并为其赋值一个新的 OleDbConnection 类，这个类带有指示 OLE DB 提供商和数据库位置的连接字符串。然后我们打开数据库连接：

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `创建数据库连接` 这一小节和 `WebForms 数据库连接` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
