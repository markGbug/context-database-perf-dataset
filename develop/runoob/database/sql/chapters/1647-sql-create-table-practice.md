# SQL：SQL CREATE TABLE 语句

- 来源：[SQL CREATE TABLE](https://www.runoob.com/sql/sql-create-table.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：练习笔记
- 章节序号：1647

## 本章内容

## SQL CREATE TABLE 语句

CREATE TABLE 语句用于创建数据库中的表。

表由行和列组成，每个表都必须有个表名。


### SQL CREATE TABLE 语法

column_name 参数规定表中列的名称。

data_type 参数规定列的数据类型（例如 varchar、integer、decimal、date 等等）。

size 参数规定表中列的最大长度。

提示：如需了解 MS Access、MySQL 和 SQL Server 中可用的数据类型，请访问我们完整的 数据类型参考手册。


## SQL CREATE TABLE 实例

现在我们想要创建一个名为 "Persons" 的表，包含五列：PersonID、LastName、FirstName、Address 和 City。

我们使用下面的 CREATE TABLE 语句：


## 实例

PersonID 列的数据类型是 int，包含整数。

LastName、FirstName、Address 和 City 列的数据类型是 varchar，包含字符，且这些字段的最大长度为 255 个字符。

空的 "Persons" 表如下所示：

提示：可使用 INSERT INTO 语句向空表写入数据。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQL CREATE TABLE` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
