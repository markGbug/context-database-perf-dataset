# SQLite：SQLite 删除表

- 来源：[SQLite 删除表](https://www.runoob.com/sqlite/sqlite-drop-table.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：练习笔记
- 章节序号：1698

## 本章内容

SQLite 的 DROP TABLE 语句用来删除表定义及其所有相关数据、索引、触发器、约束和该表的权限规范。


## 语法

DROP TABLE 语句的基本语法如下。您可以选择指定带有表名的数据库名称，如下所示：

```text
DROP TABLE database_name.table_name;
```


## 实例

让我们先确认 COMPANY 表已经存在，然后我们将其从数据库中删除。

```text
sqlite>.tables
COMPANY       test.COMPANY
```

这意味着 COMPANY 表已存在数据库中，接下来让我们把它从数据库中删除，如下：

```text
sqlite>DROP TABLE COMPANY;
sqlite>
```

现在，如果尝试 .TABLES 命令，那么将无法找到 COMPANY 表了：

```text
sqlite>.tables
sqlite>
```

显示结果为空，意味着已经成功从数据库删除表。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQLite 删除表` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
