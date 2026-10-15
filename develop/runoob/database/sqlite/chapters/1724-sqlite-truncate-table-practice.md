# SQLite：SQLite Truncate Table

- 来源：[SQLite Truncate Table](https://www.runoob.com/sqlite/sqlite-truncate-table.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：练习笔记
- 章节序号：1724

## 本章内容

在 SQLite 中，并没有 TRUNCATE TABLE 命令，但可以使用 SQLite 的 DELETE 命令从已有的表中删除全部的数据。


## 语法

DELETE 命令的基本语法如下：

```text
sqlite> DELETE FROM table_name;
```

但这种方法无法将递增数归零。

如果要将递增数归零，可以使用以下方法：

```text
sqlite> DELETE FROM sqlite_sequence WHERE name = 'table_name';
```

当 SQLite 数据库中包含自增列时，会自动建立一个名为 sqlite_sequence 的表。这个表包含两个列：name 和 seq。name 记录自增列所在的表，seq 记录当前序号（下一条记录的编号就是当前序号加 1）。如果想把某个自增列的序号归零，只需要修改 sqlite_sequence 表就可以了。

```text
UPDATE sqlite_sequence SET seq = 0 WHERE name = 'table_name';
```


## 实例

假设 COMPANY 表有如下记录：

```text
ID          NAME        AGE         ADDRESS     SALARY
----------  ----------  ----------  ----------  ----------
1           Paul        32          California  20000.0
2           Allen       25          Texas       15000.0
3           Teddy       23          Norway      20000.0
4           Mark        25          Rich-Mond   65000.0
5           David       27          Texas       85000.0
6           Kim         22          South-Hall  45000.0
7           James       24          Houston     10000.0
```

下面为删除上表记录的实例：

```text
SQLite> DELETE FROM sqlite_sequence WHERE name = 'COMPANY';
SQLite> VACUUM;
```

现在，COMPANY 表中的记录完全被删除，使用 SELECT 语句将没有任何输出。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQLite Truncate Table` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
