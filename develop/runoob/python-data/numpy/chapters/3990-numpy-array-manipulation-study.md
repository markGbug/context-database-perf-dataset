# NumPy：Numpy 数组操作

- 来源：[Numpy 数组操作](https://www.runoob.com/numpy/numpy-array-manipulation.html)
- 分类：Python / 数据科学
- 技术：NumPy
- 笔记类型：学习笔记
- 章节序号：3990

## 本章内容

Numpy 中包含了一些函数用于处理数组，大概可分为以下几类：

- 修改数组形状
- 翻转数组
- 修改数组维度
- 连接数组
- 分割数组
- 数组元素的添加与删除


## 修改数组形状


### numpy.reshape

numpy.reshape 函数可以在不改变数据的条件下修改形状，格式如下：

```text
numpy.reshape(arr, newshape, order='C')
```

- arr：要修改形状的数组
- newshape：整数或者整数数组，新的形状应当兼容原有形状
- order：'C' -- 按行，'F' -- 按列，'A' -- 原顺序，'k' -- 元素在内存中的出现顺序。


## 实例

```java
import numpy as np

a = np.arange(8)
print ('原始数组：')
print (a)
print ('\n')

b = a.reshape(4,2)
print ('修改后的数组：')
print (b)
```

输出结果如下：

```text
原始数组：
[0 1 2 3 4 5 6 7]

修改后的数组：
[[0 1]
 [2 3]
 [4 5]
 [6 7]]
```


### numpy.ndarray.flat

numpy.ndarray.flat 是一个数组元素迭代器，实例如下:


## 实例

```java
import numpy as np

a = np.arange(9).reshape(3,3)
print ('原始数组：')
for row in a:
    print (row)

#对数组中每个元素都进行处理，可以使用flat属性，该属性是一个数组元素迭代器：
print ('迭代后的数组：')
for element in a.flat:
    print (element)
```

输出结果如下：

```text
原始数组：
[0 1 2]
[3 4 5]
[6 7 8]
迭代后的数组：
0
1
2
3
4
5
6
7
8
```


### numpy.ndarray.flatten

numpy.ndarray.flatten 返回一份数组拷贝，对拷贝所做的修改不会影响原始数组，格式如下：

```text
ndarray.flatten(order='C')
```

参数说明：

- order：'C' -- 按行，'F' -- 按列，'A' -- 原顺序，'K' -- 元素在内存中的出现顺序。


## 实例

```java
import numpy as np

a = np.arange(8).reshape(2,4)

print ('原数组：')
print (a)
print ('\n')
# 默认按行

print ('展开的数组：')
print (a.flatten())
print ('\n')

print ('以 F 风格顺序展开的数组：')
print (a.flatten(order = 'F'))
```

输出结果如下：

```text
原数组：
[[0 1 2 3]
 [4 5 6 7]]


展开的数组：
[0 1 2 3 4 5 6 7]


以 F 风格顺序展开的数组：
[0 4 1 5 2 6 3 7]
```


### numpy.ravel

numpy.ravel() 展平的数组元素，顺序通常是"C风格"，返回的是数组视图（view，有点类似 C/C++引用reference的意味），修改会影响原始数组。

该函数接收两个参数：

```text
numpy.ravel(a, order='C')
```

参数说明：

- order：'C' -- 按行，'F' -- 按列，'A' -- 原顺序，'K' -- 元素在内存中的出现顺序。


## 实例

```java
import numpy as np

a = np.arange(8).reshape(2,4)

print ('原数组：')
print (a)
print ('\n')

print ('调用 ravel 函数之后：')
print (a.ravel())
print ('\n')

print ('以 F 风格顺序调用 ravel 函数之后：')
print (a.ravel(order = 'F'))
```

输出结果如下：

```text
原数组：
[[0 1 2 3]
 [4 5 6 7]]


调用 ravel 函数之后：
[0 1 2 3 4 5 6 7]


以 F 风格顺序调用 ravel 函数之后：
[0 4 1 5 2 6 3 7]
```


## 翻转数组


### numpy.transpose

numpy.transpose 函数用于对换数组的维度，格式如下：

```text
numpy.transpose(arr, axes)
```

参数说明:

- arr：要操作的数组
- axes：整数列表，对应维度，通常所有维度都会对换。


## 实例

```java
import numpy as np

a = np.arange(12).reshape(3,4)

print ('原数组：')
print (a )
print ('\n')

print ('对换数组：')
print (np.transpose(a))
```

输出结果如下：

```text
原数组：
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]


对换数组：
[[ 0  4  8]
 [ 1  5  9]
 [ 2  6 10]
 [ 3  7 11]]
```

numpy.ndarray.T 类似 numpy.transpose：


## 实例

```java
import numpy as np

a = np.arange(12).reshape(3,4)

print ('原数组：')
print (a)
print ('\n')

print ('转置数组：')
print (a.T)
```

输出结果如下：

```text
原数组：
[[ 0  1  2  3]
 [ 4  5  6  7]
 [ 8  9 10 11]]


转置数组：
[[ 0  4  8]
 [ 1  5  9]
 [ 2  6 10]
 [ 3  7 11]]
```


### numpy.rollaxis

numpy.rollaxis 函数向后滚动特定的轴到一个特定位置，格式如下：

```text
numpy.rollaxis(arr, axis, start)
```

参数说明：

- arr：数组
- axis：要向后滚动的轴，其它轴的相对位置不会改变
- start：默认为零，表示完整的滚动。会滚动到特定位置。


## 实例

```java
import numpy as np

# 创建了三维的 ndarray
a = np.arange(8).reshape(2,2,2)

print ('原数组：')
print (a)
print ('获取数组中一个值：')
print(np.where(a==6))
print(a[1,1,0])  # 为 6
print ('\n')


# 将轴 2 滚动到轴 0（宽度到深度）

print ('调用 rollaxis 函数：')
b = np.rollaxis(a,2,0)
print (b)
# 查看元素 a[1,1,0]，即 6 的坐标，变成 [0, 1, 1]
# 最后一个 0 移动到最前面
print(np.where(b==6))
print ('\n')

# 将轴 2 滚动到轴 1：（宽度到高度）

print ('调用 rollaxis 函数：')
c = np.rollaxis(a,2,1)
print (c)
# 查看元素 a[1,1,0]，即 6 的坐标，变成 [1, 0, 1]
# 最后的 0 和 它前面的 1 对换位置
print(np.where(c==6))
print ('\n')
```

输出结果如下：

```text
原数组：
[[[0 1]
  [2 3]]

 [[4 5]
  [6 7]]]
获取数组中一个值：
(array([1]), array([1]), array([0]))
6


调用 rollaxis 函数：
[[[0 2]
  [4 6]]

 [[1 3]
  [5 7]]]
(array([0]), array([1]), array([1]))


调用 rollaxis 函数：
[[[0 2]
  [1 3]]

 [[4 6]
  [5 7]]]
(array([1]), array([0]), array([1]))
```


### numpy.swapaxes

numpy.swapaxes 函数用于交换数组的两个轴，格式如下：

```text
numpy.swapaxes(arr, axis1, axis2)
```

- arr：输入的数组
- axis1：对应第一个轴的整数
- axis2：对应第二个轴的整数


## 实例

```java
import numpy as np

# 创建了三维的 ndarray
a = np.arange(8).reshape(2,2,2)

print ('原数组：')
print (a)
print ('\n')
# 现在交换轴 0（深度方向）到轴 2（宽度方向）

print ('调用 swapaxes 函数后的数组：')
print (np.swapaxes(a, 2, 0))
```

输出结果如下：

```text
原数组：
[[[0 1]
  [2 3]]

 [[4 5]
  [6 7]]]


调用 swapaxes 函数后的数组：
[[[0 4]
  [2 6]]

 [[1 5]
  [3 7]]]
```


## 修改数组维度


### numpy.broadcast

numpy.broadcast 用于模仿广播的对象，它返回一个对象，该对象封装了将一个数组广播到另一个数组的结果。

该函数使用两个数组作为输入参数，如下实例：


## 实例

```java
import numpy as np

x = np.array([[1], [2], [3]])
y = np.array([4, 5, 6])

# 对 y 广播 x
b = np.broadcast(x,y)
# 它拥有 iterator 属性，基于自身组件的迭代器元组

print ('对 y 广播 x：')
r,c = b.iters

# Python3.x 为 next(context) ，Python2.x 为 context.next()
print (next(r), next(c))
print (next(r), next(c))
print ('\n')
# shape 属性返回广播对象的形状

print ('广播对象的形状：')
print (b.shape)
print ('\n')
# 手动使用 broadcast 将 x 与 y 相加
b = np.broadcast(x,y)
c = np.empty(b.shape)

print ('手动使用 broadcast 将 x 与 y 相加：')
print (c.shape)
print ('\n')
c.flat = [u + v for (u,v) in b]

print ('调用 flat 函数：')
print (c)
print ('\n')
# 获得了和 NumPy 内建的广播支持相同的结果

print ('x 与 y 的和：')
print (x + y)
```

输出结果为：

```text
对 y 广播 x：
1 4
1 5


广播对象的形状：
(3, 3)


手动使用 broadcast 将 x 与 y 相加：
(3, 3)


调用 flat 函数：
[[5. 6. 7.]
 [6. 7. 8.]
 [7. 8. 9.]]


x 与 y 的和：
[[5 6 7]
 [6 7 8]
 [7 8 9]]
```


### numpy.broadcast_to

numpy.broadcast_to 函数将数组广播到新形状。它在原始数组上返回只读视图。 它通常不连续。 如果新形状不符合 NumPy 的广播规则，该函数可能会抛出ValueError。

```text
numpy.broadcast_to(array, shape, subok)
```


## 实例

```java
import numpy as np

a = np.arange(4).reshape(1,4)

print ('原数组：')
print (a)
print ('\n')

print ('调用 broadcast_to 函数之后：')
print (np.broadcast_to(a,(4,4)))
```

输出结果为：

```text
原数组：
[[0 1 2 3]]


调用 broadcast_to 函数之后：
[[0 1 2 3]
 [0 1 2 3]
 [0 1 2 3]
 [0 1 2 3]]
```


### numpy.expand_dims

numpy.expand_dims 函数通过在指定位置插入新的轴来扩展数组形状，函数格式如下:

```text
 numpy.expand_dims(arr, axis)
```

参数说明：

- arr：输入数组
- axis：新轴插入的位置


## 实例

```java
import numpy as np

x = np.array(([1,2],[3,4]))

print ('数组 x：')
print (x)
print ('\n')
y = np.expand_dims(x, axis = 0)

print ('数组 y：')
print (y)
print ('\n')

print ('数组 x 和 y 的形状：')
print (x.shape, y.shape)
print ('\n')
# 在位置 1 插入轴
y = np.expand_dims(x, axis = 1)

print ('在位置 1 插入轴之后的数组 y：')
print (y)
print ('\n')

print ('x.ndim 和 y.ndim：')
print (x.ndim,y.ndim)
print ('\n')

print ('x.shape 和 y.shape：')
print (x.shape, y.shape)
```

输出结果为：

```text
数组 x：
[[1 2]
 [3 4]]


数组 y：
[[[1 2]
  [3 4]]]


数组 x 和 y 的形状：
(2, 2) (1, 2, 2)


在位置 1 插入轴之后的数组 y：
[[[1 2]]

 [[3 4]]]


x.ndim 和 y.ndim：
2 3


x.shape 和 y.shape：
(2, 2) (2, 1, 2)
```


## 后续章节

- numpy.squeeze
- 实例
- 连接数组
- numpy.concatenate
- 实例
- numpy.stack
- 实例
- numpy.hstack
- 实例
- numpy.vstack
- 实例
- 分割数组
- numpy.split
- 实例
- 实例
- numpy.hsplit

## 复习重点

- 能说明 `Numpy 数组操作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
