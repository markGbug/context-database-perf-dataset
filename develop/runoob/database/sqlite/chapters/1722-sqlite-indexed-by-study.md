# SQLite：SQLite Indexed By

- 来源：[SQLite Indexed By](https://www.runoob.com/sqlite/sqlite-indexed-by.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：学习笔记
- 章节序号：1722

## 本章内容

"INDEXED BY index-name" 子句规定必须需要命名的索引来查找前面表中值。

如果索引名 index-name 不存在或不能用于查询，然后 SQLite 语句的准备失败。

"NOT INDEXED" 子句规定当访问前面的表（包括由 UNIQUE 和 PRIMARY KEY 约束创建的隐式索引）时，没有使用索引。

然而，即使指定了 "NOT INDEXED"，INTEGER PRIMARY KEY 仍然可以被用于查找条目。


## 语法

下面是 INDEXED BY 子句的语法，它可以与 DELETE、UPDATE 或 SELECT 语句一起使用：

```text
SELECT|DELETE|UPDATE column1, column2...
INDEXED BY (index_name)
table_name
WHERE (CONDITION);
```


## 实例

假设有表 COMPANY，我们将创建一个索引，并用它进行 INDEXED BY 操作。

```text
sqlite> CREATE INDEX salary_index ON COMPANY(salary);
sqlite>
```

现在使用 INDEXED BY 子句从表 COMPANY 中选择数据，如下所示：

```text
sqlite> SELECT * FROM COMPANY INDEXED BY salary_index WHERE salary > 5000;
```


## 复习重点

- 能说明 `SQLite Indexed By` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
