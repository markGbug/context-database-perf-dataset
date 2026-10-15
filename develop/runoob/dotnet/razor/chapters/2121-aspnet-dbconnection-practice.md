# Razor：ASP.NET Web Forms - 数据库连接

- 来源：[WebForms 数据库连接](https://www.runoob.com/aspnet/aspnet-dbconnection.html)
- 分类：.NET
- 技术：Razor
- 笔记类型：练习笔记
- 章节序号：2121

## 本章内容

ADO.NET 也是 .NET 框架的组成部分。ADO.NET 用于处理数据访问。通过 ADO.NET，您可以操作数据库。


## 尝试一下 - 实例

数据库连接 - 绑定到 DataList 控件

数据库连接 - 绑定到 Repeater 控件


## 什么是 ADO.NET？

- ADO.NET 是 .NET 框架的组成部分
- ADO.NET 由一系列用于处理数据访问的类组成
- ADO.NET 完全基于 XML
- ADO.NET 没有 Recordset 对象，这一点与 ADO 不同


## 创建数据库连接

在我们的实例中，我们将使用 Northwind 数据库。

首先，导入 "System.Data.OleDb" 命名空间。我们需要这个命名空间来操作 Microsoft Access 和其他 OLE DB 数据库提供商。我们将在 Page_Load 子例程中创建这个数据库的连接。我们创建一个 dbconn 变量，并为其赋值一个新的 OleDbConnection 类，这个类带有指示 OLE DB 提供商和数据库位置的连接字符串。然后我们打开数据库连接：

注释：这个连接字符串必须是没有折行的连续字符串！


## 创建数据库命令

为了指定需从数据库取回的记录，我们将创建一个 dbcomm 变量，并为其赋值一个新的 OleDbCommand 类。这个 OleDbCommand 类用于发出针对数据库表的 SQL 查询：


## 创建 DataReader

OleDbDataReader 类用于从数据源中读取记录流。DataReader 是通过调用 OleDbCommand 对象的 ExecuteReader 方法来创建的：


## 绑定到 Repeater 控件

然后，我们绑定 DataReader 到 Repeater 控件：


## 实例


## 关闭数据库连接

如果不再需要访问数据库，请记得关闭 DataReader 和数据库连接：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebForms 数据库连接` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
