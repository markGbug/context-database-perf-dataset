# Pandas：Pandas 数据结构 - DataFrame

- 来源：[Pandas DataFrame](https://www.runoob.com/pandas/pandas-dataframe.html)
- 分类：Python / 数据科学
- 技术：Pandas
- 笔记类型：练习笔记
- 章节序号：4008

## 本章内容

DataFrame 是 Pandas 中的另一个核心数据结构，类似于一个二维的表格或数据库中的数据表。

DataFrame 是一个表格型的数据结构，它含有一组有序的列，每列可以是不同的值类型（数值、字符串、布尔型值）。

DataFrame 既有行索引也有列索引，它可以被看做由 Series 组成的字典（共同用一个索引）。

DataFrame 提供了各种功能来进行数据访问、筛选、分割、合并、重塑、聚合以及转换等操作。

DataFrame 是一个非常灵活且强大的数据结构，广泛用于数据分析、清洗、转换、可视化等任务。

DataFrame 特点：

- 二维结构： DataFrame 是一个二维表格，可以被看作是一个 Excel 电子表格或 SQL 表，具有行和列。可以将其视为多个 Series 对象组成的字典。
- 列的数据类型： 不同的列可以包含不同的数据类型，例如整数、浮点数、字符串或 Python 对象等。
- 索引：DataFrame 可以拥有行索引和列索引，类似于 Excel 中的行号和列标。
- 大小可变：可以添加和删除列，类似于 Python 中的字典。
- 自动对齐：在进行算术运算或数据对齐操作时，DataFrame 会自动对齐索引。
- 处理缺失数据：DataFrame 可以包含缺失数据，Pandas 使用 NaN（Not a Number）来表示。
- 数据操作：支持数据切片、索引、子集分割等操作。
- 时间序列支持：DataFrame 对时间序列数据有特别的支持，可以轻松地进行时间数据的切片、索引和操作。
- 丰富的数据访问功能：通过 .loc、.iloc 和 .query() 方法，可以灵活地访问和筛选数据。
- 灵活的数据处理功能：包括数据合并、重塑、透视、分组和聚合等。
- 数据可视化：虽然 DataFrame 本身不是可视化工具，但它可以与 Matplotlib 或 Seaborn 等可视化库结合使用，进行数据可视化。
- 高效的数据输入输出：可以方便地读取和写入数据，支持多种格式，如 CSV、Excel、SQL 数据库和 HDF5 格式。


## 实例 - 使用列表创建

也可以使用字典来创建：


## 实例 - 使用字典创建

输出结果如下：

以下实例使用 ndarrays 创建，ndarray 的长度必须相同， 如果传递了 index，则索引的长度应等于数组的长度。如果没有传递索引，则默认情况下，索引将是range(n)，其中n是数组长度。

ndarrays 可以参考：NumPy Ndarray 对象


## 实例 - 使用 ndarrays 创建

输出结果如下：

从以上输出结果可以知道， DataFrame 数据类型一个表格，包含 rows（行） 和 columns（列）：

还可以使用字典（key/value），其中字典的 key 为列名:


## 实例 - 使用字典创建

输出结果为：

```text
   a   b     c
0  1   2   NaN
1  5  10  20.0
```

没有对应的部分数据为 NaN。

Pandas 可以使用 loc 属性返回指定行的数据，如果没有设置索引，第一行索引为 0，第二行索引为 1，以此类推：


## 实例

输出结果如下：

```text
calories    420
duration     50
Name: 0, dtype: int64
calories    380
duration     40
Name: 1, dtype: int64
```

注意：返回结果其实就是一个 Pandas Series 数据。

也可以返回多行数据，使用 [[ ... ]] 格式，... 为各行的索引，以逗号隔开：


## 实例

输出结果为：

```text
   calories  duration
0       420        50
1       380        40
```

注意：返回结果其实就是一个 Pandas DataFrame 数据。

我们可以指定索引值，如下实例：


## 实例

输出结果为：

```text
      calories  duration
day1       420        50
day2       380        40
day3       390        45
```

Pandas 可以使用 loc 属性返回指定索引对应到某一行：


## 实例

输出结果为：

```text
calories    380
duration     40
Name: day2, dtype: int64
```


## DataFrame 方法

DataFrame 的常用操作和方法如下表所示：


## 实例

输出结果为：

```html
# 查看前两行数据
     Name  Age         City
0   Alice   25     New York
1     Bob   30  Los Angeles

# 查看 DataFrame 的基本信息
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 4 entries, 0 to 3
Data columns (total 3 columns):
 #   Column  Non-Null Count  Dtype
---  ------  --------------  -----
 0   Name    4 non-null      object
 1   Age     4 non-null      int64
 2   City    4 non-null      object
dtypes: int64(1), object(2)
memory usage: 148.0+ bytes

# 获取描述统计信息
             Age
count   4.000000
mean   32.500000
std     6.454972
min    25.000000
25%    27.500000
50%    32.500000
75%    37.500000
max    40.000000

# 按年龄排序
      Name  Age         City
3    David   40     Houston
2  Charlie   35      Chicago
1      Bob   30  Los Angeles
0    Alice   25     New York

# 按标签选择行
      Name  Age         City
1     Bob   30  Los Angeles
2  Charlie   35      Chicago

# 计算分组统计（按城市分组，计算平均年龄）
City
Chicago        35.0
Houston        40.0
Los Angeles    30.0
New York       25.0
Name: Age, dtype: float64
```


## 更多 DataFrame 说明


### 创建 DataFrame

从字典创建：字典的键成为列名，值成为列数据。


## 实例

从列表的列表创建：外层列表代表行，内层列表代表列。


## 实例

从 NumPy 数组创建：提供一个二维 NumPy 数组。


## 实例

从 Series 创建 DataFrame：通过 pd.Series() 创建。


## 实例


### DataFrame 的属性和方法

DataFrame 对象有许多属性和方法，用于数据操作、索引和处理，例如：shape、columns、index、head()、tail()、info()、describe()、mean()、sum() 等。


## 实例


### 访问 DataFrame 元素

访问列：使用列名作为属性或通过 .loc[]、.iloc[] 访问，也可以使用标签或位置索引。。


## 实例

访问行：使用行的标签和 .loc[] 访问。


## 实例


### 修改 DataFrame

修改列数据：直接对列进行赋值。

```text
df['Column1'] = [10, 11, 12]
```

添加新列：给新列赋值。

```text
df['NewColumn'] = [100, 200, 300]
```

添加新行：使用 loc、append 或 concat 方法。


## 实例

注意：append() 方法在 pandas 版本 1.4.0 中已经被标记为弃用，并将在未来的版本中被移除，官方推荐使用 concat() 作为替代方法来进行数据的合并操作。

concat() 方法用于合并两个或多个 DataFrame，当你想要添加一行到另一个 DataFrame 时，可以将新行作为一个新的 DataFrame，然后使用 concat()：


## 实例


## 后续章节

- 删除 DataFrame 元素
- DataFrame 的统计分析
- DataFrame 的索引操作
- DataFrame 的布尔索引
- DataFrame 的数据类型
- DataFrame 的合并与分割
- 索引和切片
- 实例
- 注意事项

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pandas DataFrame` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
