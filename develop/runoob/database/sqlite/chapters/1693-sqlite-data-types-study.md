# SQLite：SQLite 数据类型

- 来源：[SQLite 数据类型](https://www.runoob.com/sqlite/sqlite-data-types.html)
- 分类：数据库
- 技术：SQLite
- 笔记类型：学习笔记
- 章节序号：1693

## 本章内容

SQLite 数据类型是一个用来指定任何对象的数据类型的属性。SQLite 中的每一列，每个变量和表达式都有相关的数据类型。

您可以在创建表的同时使用这些数据类型。SQLite 使用一个更普遍的动态类型系统。在 SQLite 中，值的数据类型与值本身是相关的，而不是与它的容器相关。


## SQLite 存储类

每个存储在 SQLite 数据库中的值都具有以下存储类之一：

SQLite 的存储类稍微比数据类型更普遍。INTEGER 存储类，例如，包含 6 种不同的不同长度的整数数据类型。


## SQLite 亲和(Affinity)类型

SQLite支持列的亲和类型概念。任何列仍然可以存储任何类型的数据，当数据插入时，该字段的数据将会优先采用亲缘类型作为该值的存储方式。SQLite目前的版本支持以下五种亲缘类型：


## SQLite 亲和类型(Affinity)及类型名称

下表列出了当创建 SQLite3 表时可使用的各种数据类型名称，同时也显示了相应的亲和类型：

- INT
- INTEGER
- TINYINT
- SMALLINT
- MEDIUMINT
- BIGINT
- UNSIGNED BIG INT
- INT2
- INT8
- CHARACTER(20)
- VARCHAR(255)
- VARYING CHARACTER(255)
- NCHAR(55)
- NATIVE CHARACTER(70)
- NVARCHAR(100)
- TEXT
- CLOB
- BLOB
- 未指定类型
- REAL
- DOUBLE
- DOUBLE PRECISION
- FLOAT
- NUMERIC
- DECIMAL(10,5)
- BOOLEAN
- DATE


## Boolean 数据类型

SQLite 没有单独的 Boolean 存储类。相反，布尔值被存储为整数 0（false）和 1（true）。


## Date 与 Time 数据类型

SQLite 没有一个单独的用于存储日期和/或时间的存储类，但 SQLite 能够把日期和时间存储为 TEXT、REAL 或 INTEGER 值。

您可以以任何上述格式来存储日期和时间，并且可以使用内置的日期和时间函数来自由转换不同格式。


## 复习重点

- 能说明 `SQLite 数据类型` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
