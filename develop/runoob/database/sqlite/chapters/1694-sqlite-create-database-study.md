# SQLite：SQLite 创建数据库

- 来源：[SQLite 创建数据库](https://www.runoob.com/sqlite/sqlite-create-database.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：学习笔记
- 章节序号：1694

## 本章内容

SQLite 的 sqlite3 命令被用来创建新的 SQLite 数据库。您不需要任何特殊的权限即可创建一个数据。


## 语法

sqlite3 命令的基本语法如下：

```text
$ sqlite3 DatabaseName.db
```

通常情况下，数据库名称在 RDBMS 内应该是唯一的。

另外我们也可以使用 .open 来建立新的数据库文件：

```text
sqlite>.open test.db
```

上面的命令创建了数据库文件 test.db，位于 sqlite3 命令同一目录下。

打开已存在数据库也是用 .open 命令，以上命令如果 test.db 存在则直接会打开，不存在就创建它。


## 复习重点

- 能说明 `SQLite 创建数据库` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
