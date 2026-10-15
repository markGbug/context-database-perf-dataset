# SQL：SQL Date 函数

- 来源：[SQL 日期](https://www.runoob.com/sql/sql-dates.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：练习笔记
- 章节序号：1660

## 本章内容

## SQL 日期（Dates）

当我们处理日期时，最难的任务恐怕是确保所插入的日期的格式，与数据库中日期列的格式相匹配。

只要您的数据包含的只是日期部分，运行查询就不会出问题。但是，如果涉及时间部分，情况就有点复杂了。

在讨论日期查询的复杂性之前，我们先来看看最重要的内建日期处理函数。


## MySQL Date 函数

下面的表格列出了 MySQL 中最重要的内建日期函数：


## SQL Server Date 函数

下面的表格列出了 SQL Server 中最重要的内建日期函数：


## SQL Date 数据类型

MySQL 使用下列数据类型在数据库中存储日期或日期/时间值：

- DATE - 格式：YYYY-MM-DD
- DATETIME - 格式：YYYY-MM-DD HH:MM:SS
- TIMESTAMP - 格式：YYYY-MM-DD HH:MM:SS
- YEAR - 格式：YYYY 或 YY

SQL Server 使用下列数据类型在数据库中存储日期或日期/时间值：

- DATE - 格式：YYYY-MM-DD
- DATETIME - 格式：YYYY-MM-DD HH:MM:SS
- SMALLDATETIME - 格式：YYYY-MM-DD HH:MM:SS
- TIMESTAMP - 格式：唯一的数字

注释：当您在数据库中创建一个新表时，需要为列选择数据类型！

如需了解所有可用的数据类型，请访问我们完整的 数据类型参考手册。


## SQL 日期处理

如果不涉及时间部分，那么我们可以轻松地比较两个日期！

假设我们有如下的 "Orders" 表：

现在，我们希望从上表中选取 OrderDate 为 "2008-11-11" 的记录。

我们使用下面的 SELECT 语句：

结果集如下所示：

现在，假设 "Orders" 表如下所示（请注意 "OrderDate" 列中的时间部分）：

如果我们使用和上面一样的 SELECT 语句：

```text
SELECT * FROM Orders WHERE OrderDate='2008-11-11'

或

SELECT * FROM Orders WHERE OrderDate='2008-11-11 00：00：00'
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQL 日期` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
