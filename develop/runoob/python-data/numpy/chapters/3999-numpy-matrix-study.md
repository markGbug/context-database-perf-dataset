# NumPy：NumPy 矩阵库(Matrix)

- 来源：[NumPy 矩阵库(Matrix)](https://www.runoob.com/numpy/numpy-matrix.html)
- 分类：Python / 数据科学
- 技术：NumPy
- 笔记类型：学习笔记
- 章节序号：3999

## 本章内容

NumPy 中包含了一个矩阵库 numpy.matlib，该模块中的函数返回的是一个矩阵，而不是 ndarray 对象。

numpy.matlib 专门用于创建和操作 矩阵（matrix） 对象。虽然 NumPy 的核心支持多维数组（ndarray），numpy.matlib 提供了一些方便的函数，专门返回矩阵类型，便于用户进行传统的线性代数运算。

一个 的矩阵是一个由行（row）列（column）元素排列成的矩形阵列。

矩阵里的元素可以是数字、符号或数学式。以下是一个由 6 个数字元素构成的 2 行 3 列的矩阵：


### 转置矩阵

NumPy 中除了可以使用 numpy.transpose 函数来对换数组的维度，还可以使用 T 属性。。

例如有个 m 行 n 列的矩阵，使用 t() 函数就能转换为 n 行 m 列的矩阵。


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


### matlib.empty()

matlib.empty() 函数返回一个新的矩阵，语法格式为：

```text
numpy.matlib.empty(shape, dtype, order)
```

参数说明：

- shape: 定义新矩阵形状的整数或整数元组
- Dtype: 可选，数据类型
- order: C（行序优先） 或者 F（列序优先）


## 实例

```java
import numpy.matlib
import numpy as np

print (np.matlib.empty((2,2)))
# 填充为随机数据
```

输出结果为：

```text
[[-1.49166815e-154 -1.49166815e-154]
 [ 2.17371491e-313  2.52720790e-212]]
```


### numpy.matlib.zeros()

numpy.matlib.zeros() 函数创建一个以 0 填充的矩阵。


## 实例

```java
import numpy.matlib
import numpy as np

print (np.matlib.zeros((2,2)))
```

输出结果为：

```text
[[0. 0.]
 [0. 0.]]
```


### numpy.matlib.ones()

numpy.matlib.ones()函数创建一个以 1 填充的矩阵。


## 实例

```java
import numpy.matlib
import numpy as np

print (np.matlib.ones((2,2)))
```

输出结果为：

```text
[[1. 1.]
 [1. 1.]]
```


### numpy.matlib.eye()

numpy.matlib.eye() 函数返回一个矩阵，对角线元素为 1，其他位置为零。

```text
numpy.matlib.eye(n, M,k, dtype)
```

参数说明：

- n: 返回矩阵的行数
- M: 返回矩阵的列数，默认为 n
- k: 对角线的索引
- dtype: 数据类型


## 实例

```java
import numpy.matlib
import numpy as np

print (np.matlib.eye(n =  3, M =  4, k =  0, dtype =  float))
```

输出结果为：

```text
[[1. 0. 0. 0.]
 [0. 1. 0. 0.]
 [0. 0. 1. 0.]]
```


### numpy.matlib.identity()

numpy.matlib.identity() 函数返回给定大小的单位矩阵。

单位矩阵是个方阵，从左上角到右下角的对角线（称为主对角线）上的元素均为 1，除此以外全都为 0。


## 实例

```java
import numpy.matlib
import numpy as np

# 大小为 5，类型位浮点型
print (np.matlib.identity(5, dtype =  float))
```

输出结果为：

```text
[[ 1.  0.  0.  0.  0.]
 [ 0.  1.  0.  0.  0.]
 [ 0.  0.  1.  0.  0.]
 [ 0.  0.  0.  1.  0.]
 [ 0.  0.  0.  0.  1.]]
```


### numpy.matlib.rand()

numpy.matlib.rand() 函数创建一个给定大小的矩阵，数据是随机填充的。


## 实例

```java
import numpy.matlib
import numpy as np

print (np.matlib.rand(3,3))
```

输出结果为：

```text
[[0.23966718 0.16147628 0.14162   ]
 [0.28379085 0.59934741 0.62985825]
 [0.99527238 0.11137883 0.41105367]]
```

矩阵总是二维的，而 ndarray 是一个 n 维数组。 两个对象都是可互换的。


## 实例

```java
import numpy.matlib
import numpy as np

i = np.matrix('1,2;3,4')
print (i)
```

输出结果为：

```text
[[1  2]
 [3  4]]
```


## 实例

```java
import numpy.matlib
import numpy as np

j = np.asarray(i)
print (j)
```

输出结果为：

```text
[[1  2]
 [3  4]]
```


## 实例

```java
import numpy.matlib
import numpy as np

k = np.asmatrix (j)
print (k)
```

输出结果为：

```text
[[1  2]
 [3  4]]
```

下面这些函数也存在于 NumPy 命名空间中，但它们返回的是矩阵对象。


### 注意事项

- 虽然 numpy.matlib 方便，但 NumPy 官方推荐使用 ndarray 和 @ 运算符来完成矩阵运算，因为 matrix 类型存在一些限制，且在未来版本中可能被弃用。
- 新代码建议优先使用 ndarray，以保证更好的兼容性和灵活性。


## 复习重点

- 能说明 `NumPy 矩阵库(Matrix)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
