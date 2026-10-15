# SQL：SQL DEFAULT 约束

- 来源：[SQL DEFAULT](https://www.runoob.com/sql/sql-default.html)
- 分类：数据库
- 技术：SQL
- 笔记类型：学习笔记
- 章节序号：1654

## 本章内容

DEFAULT 约束用于向列中插入默认值。

如果没有规定其他的值，那么会将默认值添加到所有的新记录。


### 语法

1、在创建表时定义 DEFAULT 约束：

```text
CREATE TABLE 表名 (
    列名 数据类型 DEFAULT 默认值
);
```

2、在现有表中添加 DEFAULT 约束：

```text
ALTER TABLE 表名
ALTER COLUMN 列名 SET DEFAULT 默认值;
```


### 实例

1、创建表时定义 DEFAULT 约束


## 实例

2、在现有表中添加 DEFAULT 约束

```text
ALTER TABLE Employees
ALTER COLUMN Salary SET DEFAULT 0.00;
```

3、插入数据时使用默认值

```text
INSERT INTO Employees (EmployeeID, FirstName, LastName)
VALUES (1, 'John', 'Doe');
```

如果未提供 HireDate 和 Salary 的值，数据库会自动使用默认值。


### 删除 DEFAULT 约束

不同数据库的删除方式有所不同：

1、SQL Server

```text
ALTER TABLE 表名
DROP CONSTRAINT 约束名;
```

2、MySQL

```text
ALTER TABLE 表名
ALTER COLUMN 列名 DROP DEFAULT;
```

3、Oracle

```text
ALTER TABLE 表名
MODIFY 列名 DEFAULT NULL;
```

4、MS Access

```text
ALTER TABLE 表名
ALTER COLUMN 列名 DROP DEFAULT;
```


### 注意事项

- DEFAULT 约束的值必须与列的数据类型兼容。
- 如果列定义为 NOT NULL 且未提供默认值，插入数据时必须显式提供值，否则会报错。
- 默认值可以是常量值、表达式或函数（如 GETDATE()）。


### 适用场景

- 为日期列设置当前日期为默认值。
- 为数值列设置初始值（如 0）。
- 为状态列设置默认状态（如 'Active'）。


## 复习重点

- 能说明 `SQL DEFAULT` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
