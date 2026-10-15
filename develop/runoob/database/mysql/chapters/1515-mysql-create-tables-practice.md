# MySQL：MySQL 创建数据表

- 来源：[MySQL 创建数据表](https://www.runoob.com/mysql/mysql-create-tables.html)
- 分类：数据库
- 技术：MySQL
- 笔记类型：练习笔记
- 章节序号：1515

## 本章内容

创建 MySQL 数据表需要以下信息：

- 表名
- 表字段名
- 定义每个表字段的数据类型


### 语法

以下为创建 MySQL 数据表的 SQL 通用语法：

```text
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);
```

参数说明：

- table_name 是你要创建的表的名称。
- column1, column2, ... 是表中的列名。
- datatype 是每个列的数据类型。

以下是一个具体的实例，创建一个用户表 users：


## 实例

实例解析：

- id: 用户 id，整数类型，自增长，作为主键。
- username: 用户名，变长字符串，不允许为空。
- email: 用户邮箱，变长字符串，不允许为空。
- birthdate: 用户的生日，日期类型。
- is_active: 用户是否已经激活，布尔类型，默认值为 true。

以上只是一个简单的实例，用到了一些常见的数据类型包括 INT, VARCHAR, DATE, BOOLEAN，你可以根据实际需要选择不同的数据类型。AUTO_INCREMENT 关键字用于创建一个自增长的列，PRIMARY KEY 用于定义主键。

如果你希望在创建表时指定数据引擎，字符集和排序规则等，可以使用 CHARACTER SET 和 COLLATE 子句：


## 实例

以上代码创建一个使用 utf8mb4 字符集和 utf8mb4_general_ci 排序规则的表。

以下例子中我们将在 RUNOOB 数据库中创建数据表 runoob_tbl：


## 实例

实例解析：

- 如果你不想字段为空可以设置字段的属性为 NOT NULL，如上实例中的 runoob_title 与 runoob_author 字段， 在操作数据库时如果输入该字段的数据为空，就会报错。
- AUTO_INCREMENT 定义列为自增的属性，一般用于主键，数值会自动加 1。
- PRIMARY KEY 关键字用于定义列为主键。 您可以使用多列来定义主键，列间以逗号 , 分隔。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MySQL 创建数据表` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
