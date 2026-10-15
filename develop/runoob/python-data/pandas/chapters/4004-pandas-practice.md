# Pandas：Pandas 教程

- 来源：[Pandas 教程](https://www.runoob.com/pandas/pandas-tutorial.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：练习笔记
- 章节序号：4004

## 本章内容

Pandas 是 Python 语言的一个扩展程序库，用于数据分析。

Pandas 名字衍生自术语 "panel data"（面板数据）和 "Python data analysis"（Python 数据分析）。

Pandas 是一个开放源码、BSD 许可的库，提供高性能、易于使用的数据结构和数据分析工具。

Pandas 一个强大的分析结构化数据的工具集，基础是 Numpy（提供高性能的矩阵运算）。


## 学习本教程前你需要了解

在开始学习 Pandas 教程之前，我们需要具备基本的 Python 基础，如果你对 Python还不了解，可以阅读我们的教程：

- Python 2.x 版本
- Python 3.x 版本
- Matplotlib 教程


## Pandas 应用

Pandas 可以从各种文件格式比如 CSV、JSON、SQL、Microsoft Excel 导入数据。

Pandas 可以对各种数据进行运算操作，比如归并、再成形、选择，还有数据清洗和数据加工特征。

Pandas 广泛应用在学术、金融、统计学等各个数据分析领域。


## Pandas 功能

Pandas 是数据分析的利器，它不仅提供了高效、灵活的数据结构，还能帮助你以极低的成本完成复杂的数据操作和分析任务。

Pandas 提供了丰富的功能，包括：

- 数据清洗：处理缺失数据、重复数据等。
- 数据转换：改变数据的形状、结构或格式。
- 数据分析：进行统计分析、聚合、分组等。
- 数据可视化：通过整合 Matplotlib 和 Seaborn 等库，可以进行数据可视化。


## 数据结构

Pandas 的主要数据结构是 Series （一维数据）与 DataFrame（二维数据）。

- Series 是一种类似于一维数组的对象，它由一组数据（各种 Numpy 数据类型）以及一组与之相关的数据标签（即索引）组成。
- DataFrame 是一个表格型的数据结构，它含有一组有序的列，每列可以是不同的值类型（数值、字符串、布尔型值）。DataFrame 既有行索引也有列索引，它可以被看做由 Series 组成的字典（共同用一个索引）。

Pandas 是 Python 数据科学领域中不可或缺的工具之一，它的灵活性和强大的功能使得数据处理和分析变得更加简单和高效。


## 第一个 pandas 实例

以下实例创建一个简单的 DataFrame：


## 实例

```text
     Name  Age
0  Google   25
1  Runoob   30
2  Taobao   35
```


## 相关链接

- Pandas 官网 https://pandas.pydata.org/
- Pandas 源代码：https://github.com/pandas-dev/pandas


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pandas 教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
