# NumPy：NumPy 数组属性

- 来源：[NumPy 数组属性](https://www.runoob.com/numpy/numpy-array-attributes.html)
- 分类：Python / 数据科学
- 技术：NumPy
- 笔记类型：练习笔记
- 章节序号：3982

## 本章内容

本章节我们将来了解 NumPy 数组的一些基本属性。

NumPy 数组的维数称为秩（rank），秩就是轴的数量，即数组的维度。

一维数组的秩为 1，二维数组的秩为 2，以此类推。

在 NumPy 中，数组的每一个维度称为一个轴（axis），也就是维度（dimensions）。

比如说，二维数组可以看作是"一维数组组成的一维数组"：外层数组的每个元素本身又是一个一维数组。

其中第 0 轴相当于是最外层数组的方向，第 1 轴是内层数组的方向，以此类推。

轴的数量——秩，就是数组的维数。

很多 NumPy 函数都支持 axis 参数。

对二维数组而言，axis=0 表示沿着第 0 轴进行操作，即对每一列进行操作；axis=1 表示沿着第 1 轴进行操作，即对每一行进行操作。

下面以一个 shape 为 (2, 3) 的二维数组为例，直观展示两个轴的方向以及各属性的含义：

axis 表示的是"沿哪个方向压缩"，而不是"第几行/第几列"：沿 axis=0 求和是把多行压成一行，因此结果是每一列的和。


## 实例

输出结果为：

```text
[5 7 9]
[ 6 15]
```

下面的交互演示可以更直观地感受两个轴的求和方向，点击按钮切换：

NumPy 数组中比较重要的 ndarray 对象属性有：


### ndarray.ndim

ndarray.ndim 用于获取数组的维度数量（即数组的轴数），也就是秩。


## 实例

输出结果为：

```text
1
3
```


### ndarray.shape

ndarray.shape 表示数组的维度，返回一个元组，这个元组的长度就是维度的数目，即 ndim 属性（秩）。

比如，一个二维数组的 shape 表示其"行数"和"列数"。

shape 元组的顺序与轴的顺序一致：第 0 个元素是第 0 轴的大小（行数），第 1 个元素是第 1 轴的大小（列数）。


## 实例

输出结果为：

```text
(2, 3)
```

ndarray.shape 也可以用于调整数组大小。


## 实例

输出结果为：

```text
[[1 2]
 [3 4]
 [5 6]]
```

NumPy 也提供了 reshape 函数来调整数组大小。


## 实例

输出结果为：

```text
[[1 2]
 [3 4]
 [5 6]]
```

两种方式的区别：直接给 a.shape 赋值会原地修改数组 a 本身；而 a.reshape(3, 2) 返回一个新的数组对象（通常与 a 共享同一份数据），a 本身保持不变。


### ndarray.size

ndarray.size 返回数组中元素的总个数，等于 shape 中各个轴上大小的乘积。


## 实例

输出结果为：

```text
(2, 3)
6
```


### ndarray.dtype

ndarray.dtype 返回数组中元素的数据类型。

dtype 对象包含类型名和元素位宽等信息，例如 int64 表示 64 位整数、float32 表示 32 位浮点数。


## 实例

输出结果为：

```text
int64
float32
```


### ndarray.real 与 ndarray.imag

ndarray.real 和 ndarray.imag 分别返回数组中每个元素的实部和虚部，主要在元素类型为复数（complex）时使用。


## 实例

输出结果为：

```text
[1. 3. 5.]
[2. 4. 6.]
```


### ndarray.itemsize

ndarray.itemsize 以字节的形式返回数组中每一个元素的大小。

例如，一个元素类型为 float64 的数组，itemsize 属性值为 8（float64 占用 64 位，每 8 位为 1 个字节，64 ÷ 8 = 8 个字节）。

又如，一个元素类型为 int32 的数组，itemsize 属性值为 4（32 ÷ 8）。

size 与 itemsize 的乘积就是数组数据占用的总字节数，也就是属性 ndarray.nbytes 的值。


## 实例

输出结果为：

```text
1
8
```


### ndarray.flags

ndarray.flags 返回 ndarray 对象的内存信息，包含以下属性：

旧版本的 UPDATEIFCOPY (U) 是 WRITEBACKIFCOPY 的旧名称，在 NumPy 1.14 中被弃用，NumPy 2.0 起已彻底移除，因此现在不应再使用它。

C_CONTIGUOUS 与 F_CONTIGUOUS 描述的是同一份数据在内存中的排列顺序，同一个二维数组有两种典型的存法：


## 实例

输出结果为：

```text
  C_CONTIGUOUS : True
  F_CONTIGUOUS : True
  OWNDATA : True
  WRITEABLE : True
  ALIGNED : True
  WRITEBACKIFCOPY : False
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `NumPy 数组属性` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
