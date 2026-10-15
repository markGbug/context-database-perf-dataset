# Pandas：Pandas 高级功能

- 来源：[Pandas 高级功能](https://www.runoob.com/pandas/pandas-advanced.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：练习笔记
- 章节序号：4022

## 本章内容

Pandas 提供了非常强大的数据操作功能，适用于复杂的数据清洗、分析、聚合和时间序列处理等任务。掌握 Pandas 的高级功能，可以大大提高数据处理和分析的效率。


## 一、数据合并与连接

Pandas 提供了多个方法来合并和连接不同的 DataFrame，例如 merge()、concat() 和 join()。这些方法常用于处理多个数据集和复杂的合并任务。


### 1. merge() — 数据库风格的连接

merge() 方法允许根据某些列对两个 DataFrame 进行合并，类似 SQL 中的 JOIN 操作。支持内连接、外连接、左连接和右连接。


## 实例

输出：

```text
   ID     Name  Age
0   1    Alice   24
1   2      Bob   27
```


### 2. concat() — 沿轴连接

concat() 用于将多个 DataFrame 沿指定轴（行或列）进行连接，常用于行合并（垂直连接）或列合并（水平连接）。


## 实例

输出：

```text
   A
0  1
1  2
2  3
3  4
4  5
5  6
```


### 3. join() — 基于索引连接

join() 方法是 Pandas 中的简化连接操作，通常用于基于索引将多个 DataFrame 连接。


## 实例

输出：

```text
   A  B
1  1  4
2  2  5
```


## 二、透视表与交叉表

Pandas 提供了 pivot_table() 方法来创建透视表，和 crosstab() 方法来计算交叉表。透视表和交叉表都非常适合数据的汇总和重新排列。


### 1. pivot_table() — 创建透视表


## 实例

输出：

```text
Category         A    B
Date
2024-01-01     100    0
2024-01-02       0  150
2024-01-03     200    0
2024-01-04       0  250
```


### 2. crosstab() — 创建交叉表


## 实例

输出：

```text
Region    East  North  South  West
Category
A           0      2      0     1
B           1      0      1     0
```


## 三、自定义函数应用

Pandas 提供了多种方法应用自定义函数，用于数据清洗和转换。


### 1. apply() — 应用函数到 DataFrame 或 Series 上

apply() 方法允许在 DataFrame 或 Series 上应用自定义函数，支持对行或列进行操作。


## 实例

输出：

```text
   A   B
0  2  10
1  4  20
2  6  30
3  8  40
```


### 2. applymap() — 在整个 DataFrame 上应用函数

applymap() 只能应用于 DataFrame，作用于 DataFrame 中的每个元素。


## 实例

输出：

```text
   A  B
0  1  16
1  4  25
2  9  36
```


### 3. map() — 应用函数到 Series 上

map() 可以对 Series 中的每个元素应用一个函数或一个映射关系。


## 实例

输出：

```text
       A
0  kitten
1   puppy
2     NaN
```


## 四、分组操作与聚合

Pandas 中的 groupby() 方法非常强大，可以用于分组聚合、转换数据和过滤数据。通过 groupby()，可以将数据根据某些条件分组，进行聚合运算，如求和、均值、计数等。


### 1. groupby() — 数据分组


## 实例

输出：

```text
Category
A    90
B    120
Name: Value, dtype: int64
```


### 2. 聚合操作（agg()）

agg() 用于执行复杂的聚合操作，可以传入多个函数来同时计算多个聚合值。


## 实例

输出：

```text
          sum  min  max
Category
A          90   10   50
B         120   20   60
```


## 后续章节

- 五、时间序列处理
- 1. date_range() — 生成时间序列
- 实例
- 2. 日期和时间的偏移
- 实例
- 3. 时间窗口操作（Rolling, Expanding）
- 实例
- 六、缺失值处理
- 实例
- 七、多重索引（MultiIndex）
- 1. 创建多重索引
- 实例
- 方法 2: pd.MultiIndex.from_product()
- 实例
- 方法 3: 使用 set_index() 创建多重索引
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pandas 高级功能` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
