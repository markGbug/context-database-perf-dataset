# Pandas：Pandas 读取 SQL 数据库

- 来源：[Pandas 读取 SQL](https://www.runoob.com/pandas/pandas-sql.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：练习笔记
- 章节序号：4013

## 本章内容

Pandas 提供了一组直接与 SQL 数据库交互的函数，可以将查询结果直接读取为 DataFrame，也可以将 DataFrame 写回数据库。这使得数据分析师无需手动处理数据库连接和结果解析，大幅简化了数据库与 Python 的交互流程。


## 核心函数概览

实际工作中推荐使用 pd.read_sql()，它会根据传入参数自动判断是执行查询还是读取整表，兼容性最好。pd.read_sql_table() 仅支持 SQLAlchemy 引擎连接，不支持原生 sqlite3 等 DB-API 连接。


## 建立数据库连接

Pandas 本身不直接连接数据库，需要借助第三方库建立连接后传入。主流方式有两种：SQLAlchemy 引擎（推荐）和 DB-API 原生连接（轻量简单）。


### 方式一：SQLAlchemy（推荐）

SQLAlchemy 是 Python 最主流的数据库工具包，支持所有主流数据库，且与 Pandas 兼容性最好：

```text
pip install sqlalchemy
```


## 实例


### 方式二：sqlite3 原生连接（仅 SQLite）

Python 内置 sqlite3 模块，无需额外安装，适合轻量级本地 SQLite 数据库：


## 实例


## pd.read_sql() 读取数据


### 基本语法

```text
pd.read_sql(sql, con, index_col=None, coerce_float=True, params=None, parse_dates=None, columns=None, chunksize=None)
```

主要参数说明：


### 1、读取整张表


## 实例


### 2、执行 SQL 查询


## 实例


### 3、参数化查询（防止 SQL 注入）

查询条件来自用户输入时，务必使用参数化查询，不要用字符串拼接 SQL：


## 实例


### 4、设置索引列


## 实例


### 5、解析日期列

数据库中存储的日期字段读取后默认是字符串类型，使用 parse_dates 参数可以直接解析为 datetime：


## 实例


## 分块读取大数据（chunksize）

当数据库表数据量很大时，一次性全部读入内存会导致 OOM（内存溢出）。使用 chunksize 参数可以将数据分批读取，每次只处理一部分：


## 实例


## pd.read_sql_query() 和 pd.read_sql_table()


### pd.read_sql_query()：只执行查询

与 pd.read_sql() 功能基本相同，但只接受 SQL 查询语句，不接受表名。参数完全一致，适合需要明确区分"查询"和"读表"操作的场景：


## 实例


### pd.read_sql_table()：读取整张表（仅 SQLAlchemy）

pd.read_sql_table() 专门用于读取整张表，支持通过参数过滤列和行，但仅支持 SQLAlchemy 引擎连接，不支持 sqlite3 等原生连接：


## 后续章节

- 实例
- 将 DataFrame 写入数据库（to_sql）
- 基本语法
- 实例
- 指定列的数据类型
- 实例
- 完整使用示例
- 实例
- 常见问题与注意事项
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pandas 读取 SQL` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
