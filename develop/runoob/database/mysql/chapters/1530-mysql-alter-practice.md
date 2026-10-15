# MySQL：MySQL ALTER 命令

- 来源：[MySQL ALTER 命令](https://www.runoob.com/mysql/mysql-alter.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：练习笔记
- 章节序号：1530

## 本章内容

当我们需要修改数据表名或者修改数据表字段时，就需要使用到 MySQL ALTER 命令。

MySQL 的 ALTER 命令用于修改数据库、表和索引等对象的结构。

ALTER 命令允许你添加、修改或删除数据库对象，并且可以用于更改表的列定义、添加约束、创建和删除索引等操作。

ALTER 命令非常强大，可以在数据库结构发生变化时进行灵活的修改和调整。

以下是 ALTER 命令的常见用法和实例：


### 1. 添加列

```text
ALTER TABLE table_name
ADD COLUMN new_column_name datatype;
```

以下 SQL 语句在 employees 表中添加了一个名为 birth_date 的日期列：


## 实例


### 2. 修改列的数据类型


## 实例

以下 SQL 语句将 employees 表中的 salary 列的数据类型修改为 DECIMAL(10,2)：


## 实例


### 3. 修改列名

```text
ALTER TABLE table_name
CHANGE COLUMN old_column_name new_column_name datatype;
```

以下 SQL 语句将 employees 表中的某个列的名字由 old_column_name 修改为 new_column_name，并且可以同时修改数据类型：


## 实例


### 4. 删除列

```text
ALTER TABLE table_name
DROP COLUMN column_name;
```

以下 SQL 语句将 employees 表中的 birth_date 列删除：


## 实例


### 5. 添加 PRIMARY KEY

```text
ALTER TABLE table_name
ADD PRIMARY KEY (column_name);
```

以下 SQL 语句在 employees 表中添加了一个主键：


## 实例


### 6. 添加 FOREIGN KEY

```text
ALTER TABLE child_table
ADD CONSTRAINT fk_name
FOREIGN KEY (column_name)
REFERENCES parent_table (column_name);
```

以下 SQL 语句在 orders 表中添加了一个外键，关联到 customers 表的 customer_id 列：


## 实例


### 7. 修改表名

```text
ALTER TABLE old_table_name
RENAME TO new_table_name;
```

以下 SQL 语句将表名由 employees 修改为 staff：


## 实例

注意：

但在使用 ALTER 命令时要格外小心，因为一些操作可能需要重建表或索引，这可能会影响数据库的性能和运行时间。

在进行重要的结构修改时，建议先备份数据，并在生产环境中谨慎操作。


## 实例

开始本章教程前让我们先创建一张表，表名为：testalter_tbl。


## 实例


### 删除，添加或修改表字段

如下命令使用了 ALTER 命令及 DROP 子句来删除以上创建表的 i 字段：

```text
mysql> ALTER TABLE testalter_tbl  DROP i;
```

如果数据表中只剩余一个字段则无法使用DROP来删除字段。

MySQL 中使用 ADD 子句来向数据表中添加列，如下实例在表 testalter_tbl 中添加 i 字段，并定义数据类型:

```text
mysql> ALTER TABLE testalter_tbl ADD i INT;
```

执行以上命令后，i 字段会自动添加到数据表字段的末尾。

```text
mysql> SHOW COLUMNS FROM testalter_tbl;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| c     | char(1) | YES  |     | NULL    |       |
| i     | int(11) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
2 rows in set (0.00 sec)
```

如果你需要指定新增字段的位置，可以使用MySQL提供的关键字 FIRST (设定位第一列)， AFTER 字段名（设定位于某个字段之后）。

尝试以下 ALTER TABLE 语句, 在执行成功后，使用 SHOW COLUMNS 查看表结构的变化：

```text
ALTER TABLE testalter_tbl DROP i;
ALTER TABLE testalter_tbl ADD i INT FIRST;
ALTER TABLE testalter_tbl DROP i;
ALTER TABLE testalter_tbl ADD i INT AFTER c;
```

FIRST 和 AFTER 关键字可用于 ADD 与 MODIFY 子句，所以如果你想重置数据表字段的位置就需要先使用 DROP 删除字段然后使用 ADD 来添加字段并设置位置。


### 修改字段类型及名称

如果需要修改字段类型及名称, 你可以在ALTER命令中使用 MODIFY 或 CHANGE 子句 。

例如，把字段 c 的类型从 CHAR(1) 改为 CHAR(10)，可以执行以下命令:

```text
mysql> ALTER TABLE testalter_tbl MODIFY c CHAR(10);
```

使用 CHANGE 子句, 语法有很大的不同。 在 CHANGE 关键字之后，紧跟着的是你要修改的字段名，然后指定新字段名及类型。尝试如下实例：

```text
mysql> ALTER TABLE testalter_tbl CHANGE i j BIGINT;
```

```text
mysql> ALTER TABLE testalter_tbl CHANGE j j INT;
```


### ALTER TABLE 对 Null 值和默认值的影响

当你修改字段时，你可以指定是否包含值或者是否设置默认值。

以下实例，指定字段 j 为 NOT NULL 且默认值为 100。

```text
mysql> ALTER TABLE testalter_tbl
    -> MODIFY j BIGINT NOT NULL DEFAULT 100;
```

如果你不设置默认值，MySQL会自动设置该字段默认为 NULL。


### 修改字段默认值

你可以使用 ALTER 来修改字段的默认值，尝试以下实例：

```text
mysql> ALTER TABLE testalter_tbl ALTER i SET DEFAULT 1000;
mysql> SHOW COLUMNS FROM testalter_tbl;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| c     | char(1) | YES  |     | NULL    |       |
| i     | int(11) | YES  |     | 1000    |       |
+-------+---------+------+-----+---------+-------+
2 rows in set (0.00 sec)
```

你也可以使用 ALTER 命令及 DROP子句来删除字段的默认值，如下实例：

```text
mysql> ALTER TABLE testalter_tbl ALTER i DROP DEFAULT;
mysql> SHOW COLUMNS FROM testalter_tbl;
+-------+---------+------+-----+---------+-------+
| Field | Type    | Null | Key | Default | Extra |
+-------+---------+------+-----+---------+-------+
| c     | char(1) | YES  |     | NULL    |       |
| i     | int(11) | YES  |     | NULL    |       |
+-------+---------+------+-----+---------+-------+
2 rows in set (0.00 sec)
Changing a Table Type:
```

修改数据表类型，可以使用 ALTER 命令及 TYPE 子句来完成。尝试以下实例，我们将表 testalter_tbl 的类型修改为 MYISAM ：

注意：查看数据表类型可以使用 SHOW TABLE STATUS 语句。

```text
mysql> ALTER TABLE testalter_tbl ENGINE = MYISAM;
mysql>  SHOW TABLE STATUS LIKE 'testalter_tbl'\G
*************************** 1. row ****************
           Name: testalter_tbl
           Type: MyISAM
     Row_format: Fixed
           Rows: 0
 Avg_row_length: 0
    Data_length: 0
Max_data_length: 25769803775
   Index_length: 1024
      Data_free: 0
 Auto_increment: NULL
    Create_time: 2007-06-03 08:04:36
    Update_time: 2007-06-03 08:04:36
     Check_time: NULL
 Create_options:
        Comment:
1 row in set (0.00 sec)
```


### 修改表名

如果需要修改数据表的名称，可以在 ALTER TABLE 语句中使用 RENAME 子句来实现。

尝试以下实例将数据表 testalter_tbl 重命名为 alter_tbl：

```text
mysql> ALTER TABLE testalter_tbl RENAME TO alter_tbl;
```

ALTER 命令还可以用来创建及删除MySQL数据表的索引，该功能我们会在接下来的章节中介绍。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MySQL ALTER 命令` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
