# Pandas：Pandas Index（索引）

- 来源：[Pandas Index 详解](https://www.runoob.com/pandas/pandas-index.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：学习笔记
- 章节序号：4025

## 本章内容

Index（索引）是 Pandas 数据结构的核心组成部分，它决定了数据的组织和访问方式。Pandas 支持多种类型的索引，从简单的 RangeIndex 到复杂的多层索引（MultiIndex），本节将详细介绍各种索引类型的使用方法。


## Index 的基本概念

Index 类似于数据库的主键或 Excel 的行号，用于唯一标识每行数据。DataFrame 有行索引（index）和列索引（columns）两部分。


## 实例


## RangeIndex

RangeIndex 是默认的整数索引，类似 Python 的 range(n)，从 0 开始递增。


### 创建与使用


## 实例


### RangeIndex 特点

- 内存占用最小
- 支持默认的整数位置访问
- 与其他索引类型转换简单


## Index 类型转换

Index 支持在多种类型之间转换。


### 转换为其他索引类型


## 实例


## 设置自定义索引

可以用 DataFrame 的列来设置行索引。


### 使用 set_index


## 实例


### 使用 index 参数创建


## 实例


## 索引操作


### 重置索引


## 实例


### 重新索引


## 实例


### 索引层级操作


## 实例


## 索引的属性与方法


### 索引属性使用示例


## 实例


## 后续章节

- 实战：使用索引提升查询效率
- 实例
- 注意事项

## 复习重点

- 能说明 `Pandas Index 详解` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
