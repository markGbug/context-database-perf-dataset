# Python：Python statistics 模块

- 来源：[Python statistics](https://www.runoob.com/python3/python-statistics.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：学习笔记
- 章节序号：4148

## 本章内容

在数据分析和科学计算中，统计学是一个非常重要的工具。

Python 提供了一个内置的 statistics 模块，专门用于处理基本的统计计算。本文将详细介绍 statistics 模块的功能和使用方法，帮助初学者快速掌握如何使用这个模块进行基本的统计分析。

statistics 模块提供了许多常用的统计函数，如均值、中位数、方差、标准差等。

要使用 statistics 函数必须先导入：

```text
import statistics
```

查看 statistics 模块中的内容:


## 常用的统计函数


### 均值（Mean）

均值是数据集中所有数值的平均值。statistics 模块提供了 mean() 函数来计算均值。


## 实例

输出：

```text
均值: 3
```


### 中位数（Median）

中位数是将数据集按大小顺序排列后位于中间位置的数值。statistics 模块提供了 median() 函数来计算中位数。


## 实例

输出：

```text
中位数: 3
```

如果数据集的长度为偶数，median() 函数会自动计算中间两个数的平均值。


## 实例

输出：

```text
中位数: 2.5
```


### 众数（Mode）

众数是数据集中出现频率最高的数值。statistics 模块提供了 mode() 函数来计算众数。


## 实例

输出：

```text
众数: 2
```

如果数据集中没有重复的数值，mode() 函数会抛出 StatisticsError 异常。


### 方差（Variance）

方差是衡量数据集中数值离散程度的指标。statistics 模块提供了 variance() 函数来计算方差。


## 实例

输出：

```text
方差: 2.5
```


### 标准差（Standard Deviation）

标准差是方差的平方根，用于衡量数据集的离散程度。statistics 模块提供了 stdev() 函数来计算标准差。


## 实例

输出：

```text
标准差: 1.5811388300841898
```


### 调和平均数（Harmonic Mean）

调和平均数是一种特殊的平均数，适用于计算速率等场景。statistics 模块提供了 harmonic_mean() 函数来计算调和平均数。


## 实例

输出：

```text
调和平均数: 1.7142857142857142
```


### 几何平均数（Geometric Mean）

几何平均数是一种用于计算增长率或比例的平均数。statistics 模块提供了 geometric_mean() 函数来计算几何平均数。


## 实例

输出：

```text
几何平均数: 2.0
```


## 其他常用函数


### 中位数低（Median Low）和中位数高（Median High）

statistics 模块还提供了 median_low() 和 median_high() 函数，分别用于计算数据集的中位数低和中位数高。


## 实例

输出：

```text
中位数低: 2
中位数高: 3
```


### 分位数（Quantiles）

分位数是将数据集分成若干等份的数值。statistics 模块提供了 quantiles() 函数来计算分位数。


## 实例

输出：

```text
四分位数: [1.5, 3.0, 4.5]
```


## math 模块方法


## 复习重点

- 能说明 `Python statistics` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
