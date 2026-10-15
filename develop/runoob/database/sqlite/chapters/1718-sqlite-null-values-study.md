# SQLite：SQLite NULL 值

- 来源：[SQLite NULL 值](https://www.runoob.com/sqlite/sqlite-null-values.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：学习笔记
- 章节序号：1718

## 本章内容

SQLite 的 NULL 是用来表示一个缺失值的项。表中的一个 NULL 值是在字段中显示为空白的一个值。

带有 NULL 值的字段是一个不带有值的字段。NULL 值与零值或包含空格的字段是不同的，理解这点是非常重要的。


## 语法

创建表时使用 NULL 的基本语法如下：

```text
SQLite> CREATE TABLE COMPANY(
   ID INT PRIMARY KEY     NOT NULL,
   NAME           TEXT    NOT NULL,
   AGE            INT     NOT NULL,
   ADDRESS        CHAR(50),
   SALARY         REAL
);
```


## 复习重点

- 能说明 `SQLite NULL 值` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
