# PHP：PHP MySQL Update

- 来源：[PHP MySQL Update](https://www.runoob.com/php/php-mysql-update.html)
- 分类：后端开发
- 技术：PHP
- 笔记类型：练习笔记
- 章节序号：1092

## 本章内容

UPDATE 语句用于中修改数据库表中的数据。


## 更新数据库中的数据

UPDATE 语句用于更新数据库表中已存在的记录。


### 语法

```text
UPDATE table_name
SET column1=value, column2=value2,...
WHERE some_column=some_value
```

注释：请注意 UPDATE 语法中的 WHERE 子句。WHERE 子句规定了哪些记录需要更新。如果您想省去 WHERE 子句，所有的记录都会被更新！

如需学习更多关于 SQL 的知识，请访问我们的 SQL 教程。

为了让 PHP 执行上面的语句，我们必须使用 mysqli_query() 函数。该函数用于向 MySQL 连接发送查询或命令。


### 实例

在本教程的前面章节中，我们创建了一个名为 "Persons" 的表，如下所示：

下面的例子更新 "Persons" 表的一些数据：


## 实例

在这次更新后，"Persons" 表如下所示：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `PHP MySQL Update` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
