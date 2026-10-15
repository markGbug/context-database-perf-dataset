# SQL：SQL SELECT INTO 语句

- 来源：[SQL SELECT INTO](https://www.runoob.com/sql/sql-select-into.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：练习笔记
- 章节序号：1644

## 本章内容

通过 SQL，您可以从一个表复制信息到另一个表。

SELECT INTO 语句从一个表复制数据，然后把数据插入到另一个新表中。


## SQL SELECT INTO 语句

SELECT INTO 语句从一个表复制数据，然后把数据插入到另一个新表中。

注意：

MySQL 数据库不支持 SELECT ... INTO 语句，但支持 INSERT INTO ... SELECT 。

当然你可以使用以下语句来拷贝表结构及数据：

```text
CREATE TABLE 新表
AS
SELECT * FROM 旧表
```


### SQL SELECT INTO 语法

假设有一个名为 employees 的表，包含以下数据：

要创建一个名为 employees_backup 的新表，并将 employees 表中的所有数据插入到新表中，可以使用以下 SQL 语句：

```text
SELECT *
INTO employees_backup
FROM employees;
```

执行此语句后，新的 employees_backup 表将仅包含年龄大于 25 岁的员工的数据。

```text
SELECT EmployeeID, FirstName, LastName, Age, Department
INTO employees_backup
FROM employees
WHERE Age > 25;
```


### 使用注意事项

表结构：

- SELECT INTO 会创建一个新表，并且新表的结构将基于选择的列和数据类型。
- 如果新表已经存在，SELECT INTO 语句将失败。在这种情况下，可以使用 INSERT INTO ... SELECT 语句。

数据库支持：

- SELECT INTO 语句在 SQL Server 中非常常用，但在 MySQL 和 PostgreSQL 中通常使用 CREATE TABLE ... AS SELECT 语句。


## 在其他数据库中的替代方案


### MySQL 和 PostgreSQL

在 MySQL 和 PostgreSQL 中，可以使用 CREATE TABLE ... AS SELECT 来实现类似的功能：

```text
CREATE TABLE employees_backup AS
SELECT EmployeeID, FirstName, LastName, Age, Department
FROM employees
WHERE Age > 25;
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQL SELECT INTO` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
