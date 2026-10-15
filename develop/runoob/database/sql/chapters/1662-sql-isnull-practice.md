# SQL：SQL NULL 函数

- 来源：[SQL NULL 函数](https://www.runoob.com/sql/sql-isnull.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：练习笔记
- 章节序号：1662

## 本章内容

## SQL ISNULL()、NVL()、IFNULL() 和 COALESCE() 函数

请看下面的 "Products" 表：

假如 "UnitsOnOrder" 是可选的，而且可以包含 NULL 值。

我们使用下面的 SELECT 语句：

在上面的实例中，如果有 "UnitsOnOrder" 值是 NULL，那么结果是 NULL。

微软的 ISNULL() 函数用于规定如何处理 NULL 值。

NVL()、IFNULL() 和 COALESCE() 函数也可以达到相同的结果。

在这里，我们希望 NULL 值为 0。

下面，如果 "UnitsOnOrder" 是 NULL，则不会影响计算，因为如果值是 NULL 则 ISNULL() 返回 0：

SQL Server / MS Access

Oracle

Oracle 没有 ISNULL() 函数。不过，我们可以使用 NVL() 函数达到相同的结果：

MySQL

MySQL 也拥有类似 ISNULL() 的函数。不过它的工作方式与微软的 ISNULL() 函数有点不同。

在 MySQL 中，我们可以使用 IFNULL() 函数，如下所示：

或者我们可以使用 COALESCE() 函数，如下所示：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQL NULL 函数` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
