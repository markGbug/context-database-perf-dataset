# Pandas：Pandas 读取 Parquet / Feather 文件

- 来源：[Pandas Parquet / Feather](https://www.runoob.com/pandas/pandas-parquet-feather.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：练习笔记
- 章节序号：4015

## 本章内容

Parquet 和 Feather 是两种高效的列式数据存储格式，专为大数据分析和快速读写场景设计。相比 CSV，它们具有更好的压缩比和查询性能。


## 为什么使用 Parquet 和 Feather

列式存储格式的主要优势：

Parquet 是 Apache 基金会的项目，被广泛用于大数据生态（Hadoop、Spark、DuckDB 等）。Feather 是 Arrow 项目的原生实现，专注于极致的读写速度。


## Parquet 文件操作


### 安装依赖

```text
pip install pyarrow fastparquet
```

PyArrow 和 FastParquet 都是 Parquet 的 Python 实现，PyArrow 是默认选项，FastParquet 在某些场景下更快。


### 读取 Parquet 文件


## 实例


### 写入 Parquet 文件


## 实例


### 使用快 Parquet 引擎


## 实例


## Feather 文件操作

Feather 是 Arrow 项目的 Python 实现，专注于极致的内存读写速度。


### 安装依赖

```text
pip install pyarrow
```


### 读取 Feather 文件


## 实例


### 写入 Feather 文件


## 实例


## 性能对比测试


## 实例


## 使用场景与选择建议


## 常见问题

1、读取 Parquet 报错

确保安装了 pyarrow 或 fastparquet：pip install pyarrow

2、文件损坏

写入时确保数据完整写入磁盘，建议写入后验证文件可读性。

3、版本兼容

不同版本的 Parquet 可能存在兼容性问题，建议在项目中使用固定版本。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pandas Parquet / Feather` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
