# SQLite：SQLite 命令

- 来源：[SQLite 命令](https://www.runoob.com/sqlite/sqlite-commands.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：学习笔记
- 章节序号：1691

## 本章内容

本章将向您讲解 SQLite 编程人员所使用的简单却有用的命令。这些命令被称为 SQLite 的点命令，这些命令的不同之处在于它们不以分号 ; 结束。

让我们在命令提示符下键入一个简单的 sqlite3 命令，在 SQLite 命令提示符下，您可以使用各种 SQLite 命令。

```text
$ sqlite3
SQLite version 3.3.6
Enter ".help" for instructions
sqlite>
```

如需获取可用的点命令的清单，可以在任何时候输入 ".help"。例如：

```text
sqlite>.help
```

上面的命令会显示各种重要的 SQLite 点命令的列表，如下所示：

- csv 逗号分隔的值
- column 左对齐的列
- html HTML 的 <table> 代码
- insert TABLE 表的 SQL 插入（insert）语句
- line 每行一个值
- list 由 .separator 字符串分隔的值
- tabs 由 Tab 分隔的值
- tcl TCL 列表元素

让我们尝试使用 .show 命令，来查看 SQLite 命令提示符的默认设置。

```text
sqlite>.show
     echo: off
  explain: off
  headers: off
     mode: column
nullvalue: ""
   output: stdout
separator: "|"
    width:
sqlite>
```


## 格式化输出

您可以使用下列的点命令来格式化输出为本教程下面所列出的格式：

```text
sqlite>.header on
sqlite>.mode column
sqlite>.timer on
sqlite>
```

上面设置将产生如下格式的输出：

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
CPU Time: user 0.000000 sys 0.000000
```


## sqlite_master 表格

主表中保存数据库表的关键信息，并把它命名为 sqlite_master。如要查看表概要，可按如下操作：

```text
sqlite>.schema sqlite_master
```

这将产生如下结果：

```text
CREATE TABLE sqlite_master (
  type text,
  name text,
  tbl_name text,
  rootpage integer,
  sql text
);
```


## 复习重点

- 能说明 `SQLite 命令` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
