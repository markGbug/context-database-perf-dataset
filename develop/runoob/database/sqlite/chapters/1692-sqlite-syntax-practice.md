# SQLite：SQLite 语法

- 来源：[SQLite 语法](https://www.runoob.com/sqlite/sqlite-syntax.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：练习笔记
- 章节序号：1692

## 本章内容

SQLite 是遵循一套独特的称为语法的规则和准则。本教程列出了所有基本的 SQLite 语法，向您提供了一个 SQLite 快速入门。


## 大小写敏感性

有个重要的点值得注意，SQLite 是不区分大小写的，但也有一些命令是大小写敏感的，比如 GLOB 和 glob 在 SQLite 的语句中有不同的含义。


## 注释

SQLite 注释是附加的注释，可以在 SQLite 代码中添加注释以增加其可读性，他们可以出现在任何空白处，包括在表达式内和其他 SQL 语句的中间，但它们不能嵌套。

SQL 注释以两个连续的 "-" 字符（ASCII 0x2d）开始，并扩展至下一个换行符（ASCII 0x0a）或直到输入结束，以先到者为准。

您也可以使用 C 风格的注释，以 "/*" 开始，并扩展至下一个 "*/" 字符对或直到输入结束，以先到者为准。SQLite的注释可以跨越多行。

```text
sqlite>.help -- 这是一个简单的注释
```


## SQLite 语句

所有的 SQLite 语句可以以任何关键字开始，如 SELECT、INSERT、UPDATE、DELETE、ALTER、DROP 等，所有的语句以分号 ; 结束。


## SQLite ANALYZE 语句：

```text
ANALYZE;
or
ANALYZE database_name;
or
ANALYZE database_name.table_name;
```


## SQLite AND/OR 子句：

```text
SELECT column1, column2....columnN
FROM   table_name
WHERE  CONDITION-1 {AND|OR} CONDITION-2;
```


## SQLite ALTER TABLE 语句：

```text
ALTER TABLE table_name ADD COLUMN column_def...;
```


## SQLite ALTER TABLE 语句（Rename）：

```text
ALTER TABLE table_name RENAME TO new_table_name;
```


## SQLite ATTACH DATABASE 语句：

```text
ATTACH DATABASE 'DatabaseName' As 'Alias-Name';
```


## SQLite BEGIN TRANSACTION 语句：

```text
BEGIN;
or
BEGIN EXCLUSIVE TRANSACTION;
```


## SQLite BETWEEN 子句：

```text
SELECT column1, column2....columnN
FROM   table_name
WHERE  column_name BETWEEN val-1 AND val-2;
```


## SQLite COMMIT 语句：

```text
COMMIT;
```


## SQLite CREATE INDEX 语句：

```text
CREATE INDEX index_name
ON table_name ( column_name COLLATE NOCASE );
```


## SQLite CREATE UNIQUE INDEX 语句：

```text
CREATE UNIQUE INDEX index_name
ON table_name ( column1, column2,...columnN);
```


## SQLite CREATE TABLE 语句：

```text
CREATE TABLE table_name(
   column1 datatype,
   column2 datatype,
   column3 datatype,
   .....
   columnN datatype,
   PRIMARY KEY( one or more columns )
);
```


## SQLite CREATE TRIGGER 语句：

```text
CREATE TRIGGER database_name.trigger_name
BEFORE INSERT ON table_name FOR EACH ROW
BEGIN
   stmt1;
   stmt2;
   ....
END;
```


## SQLite CREATE VIEW 语句：

```text
CREATE VIEW database_name.view_name  AS
SELECT statement....;
```


## SQLite CREATE VIRTUAL TABLE 语句：

```text
CREATE VIRTUAL TABLE database_name.table_name USING weblog( access.log );
or
CREATE VIRTUAL TABLE database_name.table_name USING fts3( );
```


## SQLite COMMIT TRANSACTION 语句：

```text
COMMIT;
```


## SQLite COUNT 子句：

```text
SELECT COUNT(column_name)
FROM   table_name
WHERE  CONDITION;
```


## SQLite DELETE 语句：

```text
DELETE FROM table_name
WHERE  {CONDITION};
```


## SQLite DETACH DATABASE 语句：

```text
DETACH DATABASE 'Alias-Name';
```


## SQLite DISTINCT 子句：

```text
SELECT DISTINCT column1, column2....columnN
FROM   table_name;
```


## SQLite DROP INDEX 语句：

```text
DROP INDEX database_name.index_name;
```


## SQLite DROP TABLE 语句：

```text
DROP TABLE database_name.table_name;
```


## 后续章节

- SQLite DROP VIEW 语句：
- SQLite DROP TRIGGER 语句：
- SQLite EXISTS 子句：
- SQLite EXPLAIN 语句：
- SQLite GLOB 子句：
- SQLite GROUP BY 子句：
- SQLite HAVING 子句：
- SQLite INSERT INTO 语句：
- SQLite IN 子句：
- SQLite Like 子句：
- SQLite NOT IN 子句：
- SQLite ORDER BY 子句：
- SQLite PRAGMA 语句：
- SQLite RELEASE SAVEPOINT 语句：
- SQLite REINDEX 语句：
- SQLite ROLLBACK 语句：

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SQLite 语法` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
