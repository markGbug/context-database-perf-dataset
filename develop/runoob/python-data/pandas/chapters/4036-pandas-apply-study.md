# Pandas：Pandas apply / map / applymap

- 来源：[Pandas apply / map / applymap](https://www.runoob.com/pandas/pandas-apply.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：学习笔记
- 章节序号：4036

## 本章内容

apply、map 和 applymap 是 Pandas 中用于数据转换的三大函数，它们可以对 DataFrame 或 Series 进行灵活的逐元素或批量操作。


## Series.map

map 是 Series 的方法，用于对 Series 中的每个元素进行转换。


### 基本用法


## 实例


### 处理缺失值


## 实例


## DataFrame.applymap

applymap 是 DataFrame 的方法，对每个元素逐个应用函数（注意：Pandas 2.0+ 推荐使用 DataFrame.map 代替）。


## 实例

applymap 逐元素操作，对于大数据可能会比较慢。如果只需要对数值列操作，考虑使用向量化操作或 apply 配合 axis 参数。


## DataFrame.apply

apply 是最灵活的方法，可以沿着坐标轴应用函数。


### 按列应用


## 实例


### 按行应用


## 实例


### 使用 aggfunc 聚合


## 实例


## Series.apply

Series 同样可以使用 apply，功能与 map 类似但更灵活。


## 实例


## 性能对比


## 实例


## 实战：数据转换


## 实例


## 三者的选择

能用向量化操作（直接用运算符）的情况下不要用 apply/map，能用 map 的情况下不要用 apply。


## 复习重点

- 能说明 `Pandas apply / map / applymap` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
