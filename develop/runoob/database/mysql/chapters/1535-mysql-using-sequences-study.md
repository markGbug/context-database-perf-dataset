# MySQL：MySQL 序列使用（AUTO_INCREMENT）

- 来源：[MySQL 序列](https://www.runoob.com/mysql/mysql-using-sequences.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：学习笔记
- 章节序号：1535

## 本章内容

在 MySQL 中，序列是一种自增生成数字序列的对象，是一组整数 1、2、3、...，由于一张数据表只能有一个字段自增主键。

尽管 MySQL 本身并没有内建的序列类型，但可以使用 AUTO_INCREMENT 属性来模拟序列的行为，通常 AUTO_INCREMENT 属性用于指定表中某一列的自增性。

一个使用 AUTO_INCREMENT 创建表的例子：


## 实例

以上例子中，id 列被定义为 INT AUTO_INCREMENT，这表示每次插入一行数据时，id 列的值会自动增加。主键约束保证了 id 列的唯一性。

当你插入一行数据时，可以不指定 id 列的值，数据库会自动为其分配一个唯一的、自增的值：

```text
INSERT INTO example_table (name) VALUES ('John');
```

你也可以使用 LAST_INSERT_ID() 函数来获取刚刚插入的行的自增值：

```text
SELECT LAST_INSERT_ID();
```

如果你需要获取表的当前自增值，可以使用以下语句：

```text
SHOW TABLE STATUS LIKE 'example_table';
```

在结果集中，Auto_increment 列的值即为当前表的自增值。

请注意，使用 AUTO_INCREMENT 属性的列只能是整数类型（通常是 INT 或 BIGINT）。此外，如果你删除表中的某一行，其自增值不会被重新使用，而是会继续递增。如果你希望手动设置自增值，可以使用 SET 语句，但这不是一种常规的做法，因为可能引起唯一性冲突。


## 使用 AUTO_INCREMENT

MySQL 中最简单使用序列的方法就是使用 MySQL AUTO_INCREMENT 来定义序列。


### 实例

以下实例中创建了数据表 insect， insect 表中 id 无需指定值可实现自动增长。

```text
mysql> CREATE TABLE insect
    -> (
    -> id INT UNSIGNED NOT NULL AUTO_INCREMENT,
    -> PRIMARY KEY (id),
    -> name VARCHAR(30) NOT NULL, # type of insect
    -> date DATE NOT NULL, # date collected
    -> origin VARCHAR(30) NOT NULL # where collected
);
Query OK, 0 rows affected (0.02 sec)
mysql> INSERT INTO insect (id,name,date,origin) VALUES
    -> (NULL,'housefly','2001-09-10','kitchen'),
    -> (NULL,'millipede','2001-09-10','driveway'),
    -> (NULL,'grasshopper','2001-09-10','front yard');
Query OK, 3 rows affected (0.02 sec)
Records: 3  Duplicates: 0  Warnings: 0
mysql> SELECT * FROM insect ORDER BY id;
+----+-------------+------------+------------+
| id | name        | date       | origin     |
+----+-------------+------------+------------+
|  1 | housefly    | 2001-09-10 | kitchen    |
|  2 | millipede   | 2001-09-10 | driveway   |
|  3 | grasshopper | 2001-09-10 | front yard |
+----+-------------+------------+------------+
3 rows in set (0.00 sec)
```


## 获取 AUTO_INCREMENT 值

在 MySQL 的客户端中你可以使用 SQL 中的 LAST_INSERT_ID() 函数来获取最后的插入表中的自增列的值。

在 PHP 或 PERL 脚本中也提供了相应的函数来获取最后的插入表中的自增列的值。


### PERL 实例

使用 mysql_insertid 属性来获取 AUTO_INCREMENT 的值。 实例如下：

```text
$dbh->do ("INSERT INTO insect (name,date,origin)
VALUES('moth','2001-09-14','windowsill')");
my $seq = $dbh->{mysql_insertid};
```


### PHP 实例


## 复习重点

- 能说明 `MySQL 序列` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
