# SQL：SQL NOT NULL 约束

- 来源：[SQL NOT NULL](https://www.runoob.com/sql/sql-notnull.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：练习笔记
- 章节序号：1649

## 本章内容

在默认的情况下，表的列接受 NULL 值。


## SQL NOT NULL 约束

NOT NULL 约束强制列不接受 NULL 值。

NOT NULL 约束强制字段始终包含值。这意味着，如果不向字段添加值，就无法插入新记录或者更新记录。

下面的 SQL 强制 "ID" 列、 "LastName" 列以及 "FirstName" 列不接受 NULL 值：


## 实例

```java
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
```


### 添加 NOT NULL 约束

在一个已创建的表的 "Age" 字段中添加 NOT NULL 约束如下所示：


## 实例

```java
ALTER TABLE Persons
MODIFY Age int NOT NULL;
```


### 删除 NOT NULL 约束

在一个已创建的表的 "Age" 字段中删除 NOT NULL 约束如下所示：


## 实例

```java
ALTER TABLE Persons
MODIFY Age int NULL;
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQL NOT NULL` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
