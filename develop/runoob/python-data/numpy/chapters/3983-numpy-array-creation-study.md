# NumPy：NumPy 创建数组

- 来源：[NumPy 创建数组](https://www.runoob.com/numpy/numpy-array-creation.html)
- 分类：Python / 数据科学
- 技术：NumPy
- 笔记类型：学习笔记
- 章节序号：3983

## 本章内容

ndarray 数组除了可以使用底层 ndarray 构造器来创建外，也可以通过以下几种方式来创建。


### numpy.empty

numpy.empty 方法用来创建一个指定形状（shape）、数据类型（dtype）且未初始化的数组：

```text
numpy.empty(shape, dtype = float, order = 'C')
```

参数说明：

下面是一个创建空数组的实例：


## 实例

```java
import numpy as np
x = np.empty([3,2], dtype = int)
print (x)
```

输出结果为：

```text
[[ 6917529027641081856  5764616291768666155]
 [ 6917529027641081859 -5764598754299804209]
 [          4497473538      844429428932120]]
```

注意 − 数组元素为随机值，因为它们未初始化。


### numpy.zeros

创建指定大小的数组，数组元素以 0 来填充：

```text
numpy.zeros(shape, dtype = float, order = 'C')
```

参数说明：


## 实例

```text
import numpy as np

# 默认为浮点数
x = np.zeros(5)
print(x)

# 设置类型为整数
y = np.zeros((5,), dtype = int)
print(y)

# 自定义类型
z = np.zeros((2,2), dtype = [('x', 'i4'), ('y', 'i4')])
print(z)
```

输出结果为：

```text
[0. 0. 0. 0. 0.]
[0 0 0 0 0]
[[(0, 0) (0, 0)]
 [(0, 0) (0, 0)]]
```


### numpy.ones

创建指定形状的数组，数组元素以 1 来填充：

```text
numpy.ones(shape, dtype = None, order = 'C')
```

参数说明：


## 实例

```text
import numpy as np

# 默认为浮点数
x = np.ones(5)
print(x)

# 自定义类型
x = np.ones([2,2], dtype = int)
print(x)
```

输出结果为：

```text
[1. 1. 1. 1. 1.]
[[1 1]
 [1 1]]
```


### numpy.zeros_like

numpy.zeros_like 用于创建一个与给定数组具有相同形状的数组，数组元素以 0 来填充。

numpy.zeros 和 numpy.zeros_like 都是用于创建一个指定形状的数组，其中所有元素都是 0。

它们之间的区别在于：numpy.zeros 可以直接指定要创建的数组的形状，而 numpy.zeros_like 则是创建一个与给定数组具有相同形状的数组。

```text
numpy.zeros_like(a, dtype=None, order='K', subok=True, shape=None)
```

参数说明：

创建一个与 arr 形状相同的，所有元素都为 0 的数组：


## 实例

```text
import numpy as np

# 创建一个 3x3 的二维数组
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

# 创建一个与 arr 形状相同的，所有元素都为 0 的数组
zeros_arr = np.zeros_like(arr)
print(zeros_arr)
```

输出结果为：

```text
[[0 0 0]
 [0 0 0]
 [0 0 0]]
```


### numpy.ones_like

numpy.ones_like 用于创建一个与给定数组具有相同形状的数组，数组元素以 1 来填充。

numpy.ones 和 numpy.ones_like 都是用于创建一个指定形状的数组，其中所有元素都是 1。

它们之间的区别在于：numpy.ones 可以直接指定要创建的数组的形状，而 numpy.ones_like 则是创建一个与给定数组具有相同形状的数组。

```text
numpy.ones_like(a, dtype=None, order='K', subok=True, shape=None)
```

参数说明：

创建一个与 arr 形状相同的，所有元素都为 1 的数组：


## 实例

```text
import numpy as np

# 创建一个 3x3 的二维数组
arr = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

# 创建一个与 arr 形状相同的，所有元素都为 1 的数组
ones_arr = np.ones_like(arr)
print(ones_arr)
```

输出结果为：

```text
[[1 1 1]
 [1 1 1]
 [1 1 1]]
```


## 复习重点

- 能说明 `NumPy 创建数组` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
