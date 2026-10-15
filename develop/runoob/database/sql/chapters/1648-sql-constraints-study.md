# SQL：SQL 约束（Constraints）

- 来源：[SQL 约束](https://www.runoob.com/sql/sql-constraints.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：学习笔记
- 章节序号：1648

## 本章内容

## SQL 约束（Constraints）

SQL 约束用于规定表中的数据规则。

如果存在违反约束的数据行为，行为会被约束终止。

约束可以在创建表时规定（通过 CREATE TABLE 语句），或者在表创建之后规定（通过 ALTER TABLE 语句）。


### SQL CREATE TABLE + CONSTRAINT 语法

```text
CREATE TABLE table_name
(
    column_name1 data_type(size) constraint_name,
    column_name2 data_type(size) constraint_name,
    column_name3 data_type(size) constraint_name,
    ....
);
```

在 SQL 中，我们有如下约束：

- NOT NULL - 指示某列不能存储 NULL 值。
- UNIQUE - 保证某列的每行必须有唯一的值。
- PRIMARY KEY - NOT NULL 和 UNIQUE 的结合。确保某列（或两个列多个列的结合）有唯一标识，有助于更容易更快速地找到表中的一个特定的记录。
- FOREIGN KEY - 保证一个表中的数据匹配另一个表中的值的参照完整性。
- CHECK - 保证列中的值符合指定的条件。
- DEFAULT - 规定没有给列赋值时的默认值。
- INDEX - 用于快速访问数据库表中的数据。


### 1. NOT NULL

确保列不能有 NULL 值。


## 实例


### 2. UNIQUE

确保列中的所有值都是唯一的。


## 实例


### 3. PRIMARY KEY

唯一标识表中的每一行记录。PRIMARY KEY 约束是 NOT NULL 和 UNIQUE 的结合。


## 实例


### 4. FOREIGN KEY

确保一个表中的值匹配另一个表中的值，从而建立两表之间的关系。


## 实例


### 5. CHECK


### 确保列中的值满足特定的条件。


## 实例


### 6. DEFAULT

为列设置默认值。


## 实例


### 7. INDEX


### 用于快速访问数据库表中的数据。

```text
CREATE INDEX idx_lastname ON Employees (LastName);
```


### 综合示例


## 实例

通过这些约束，数据库管理系统能够确保数据的一致性、完整性和准确性。

在下面的章节，我们会详细讲解每一种约束。


## 复习重点

- 能说明 `SQL 约束` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
