# Pandas：Pandas 数据排序与聚合

- 来源：[Pandas 数据排序与聚合](https://www.runoob.com/pandas/pandas-sorting.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：学习笔记
- 章节序号：4020

## 本章内容

数据排序与聚合是数据分析中非常常见且重要的操作，特别是在大数据集中的数据分析时。

排序帮助我们按特定标准对数据进行排列，而聚合则让我们对数据进行汇总，计算出各种统计量。

Pandas 提供了强大的排序和聚合功能，能够帮助分析人员高效地处理数据。


## 一、数据排序（Sorting）

排序是指将数据按某个列的值进行升序或降序排列。Pandas 提供了两种主要的方法来进行排序：sort_values() 和 sort_index()。


### 排序方法

- sort_values()：根据列的值进行排序。
- sort_index()：根据行或列的索引进行排序。


### 实例

sort_values() 示例:


## 实例

输出：

```text
Name  Age  Salary
3    David   40   80000
2  Charlie   35   70000
1      Bob   30   60000
0    Alice   25   50000
```

sort_index() 示例:


## 实例

输出：

```text
      Name  Age  Salary
0    Alice   25   50000
1      Bob   30   60000
2  Charlie   35   70000
3    David   40   80000
```


## 二、数据聚合（Aggregation）

聚合是将数据按某些规则进行汇总，通常是对某些列的数据进行求和、求平均数、求最大值、求最小值等操作。Pandas 提供了groupby()方法来对数据进行分组，然后应用不同的聚合函数。


### 聚合方法

- groupby()：按某些列分组。
- 聚合函数：如 sum(), mean(), count(), min(), max(), std() 等。


### 实例

groupby() 示例:


## 实例

输出：

```text
Department
Finance    60000.0
HR         52500.0
IT         72500.0
Name: Salary, dtype: float64
```

多重聚合函数应用:


## 实例

输出：

```text
              Salary
               mean    sum
Department
Finance    60000.0  60000
HR         52500.0  105000
IT         72500.0  145000
```


## 三、分组后的排序

聚合后的数据可以进一步按某列的值进行排序，这样可以找出特定组中最重要的值。


### 分组后排序

分组后排序示例:


## 实例

输出：

```text
    Department Employee  Salary
Department
Finance     Bob   60000
HR          Charlie  55000
HR          Alice  50000
IT          Eve   75000
IT          David  70000
```


## 四、透视表

透视表（Pivot Table）是一个特殊的聚合方式，可以让我们通过行、列和聚合函数对数据进行快速汇总，类似于 Excel 中的透视表。


### 实例

透视表示例：


## 实例

输出：

```text
Department
Finance    60000.0
HR         52500.0
IT         72500.0
Name: Salary, dtype: float64
```


## 复习重点

- 能说明 `Pandas 数据排序与聚合` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
