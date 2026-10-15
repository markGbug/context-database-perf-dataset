# NumPy：NumPy 从已有的数组创建数组

- 来源：[NumPy 从已有的数组创建数组](https://www.runoob.com/numpy/numpy-array-from-existing-data.html)
- 分类：Python / 数据科学
- 技术：NumPy
- 笔记类型：学习笔记
- 章节序号：3984

## 本章内容

本章节我们将学习如何从已有的数组创建数组。


### numpy.asarray

numpy.asarray 类似 numpy.array，但 numpy.asarray 参数只有三个，比 numpy.array 少两个。

```text
numpy.asarray(a, dtype = None, order = None)
```

参数说明：


### 实例

将列表转换为 ndarray:


## 实例

```java
import numpy as np

x =  [1,2,3]
a = np.asarray(x)
print (a)
```

输出结果为：

```text
[1  2  3]
```

将元组转换为 ndarray:


## 实例

```java
import numpy as np

x =  (1,2,3)
a = np.asarray(x)
print (a)
```

输出结果为：

```text
[1  2  3]
```

将元组列表转换为 ndarray:


## 实例

```java
import numpy as np

x =  [(1,2,3),(4,5)]
a = np.asarray(x)
print (a)
```

输出结果为：

```text
[(1, 2, 3) (4, 5)]
```

设置了 dtype 参数：


## 实例

```java
import numpy as np

x =  [1,2,3]
a = np.asarray(x, dtype =  float)
print (a)
```

输出结果为：

```text
[ 1.  2.  3.]
```


### numpy.frombuffer

numpy.frombuffer 用于实现动态数组。

numpy.frombuffer 接受 buffer 输入参数，以流的形式读入转化成 ndarray 对象。

```text
numpy.frombuffer(buffer, dtype = float, count = -1, offset = 0)
```

注意：buffer 是字符串的时候，Python3 默认 str 是 Unicode 类型，所以要转成 bytestring 在原 str 前加上 b。

参数说明：


## Python3.x 实例

```java
import numpy as np

s =  b'Hello World'
a = np.frombuffer(s, dtype =  'S1')
print (a)
```

输出结果为：

```text
[b'H' b'e' b'l' b'l' b'o' b' ' b'W' b'o' b'r' b'l' b'd']
```


## Python2.x 实例

```java
import numpy as np
s =  'Hello World'
a = np.frombuffer(s, dtype =  'S1')
print (a)
```

输出结果为：

```text
['H' 'e' 'l' 'l' 'o' ' ' 'W' 'o' 'r' 'l' 'd']
```


### numpy.fromiter

numpy.fromiter 方法从可迭代对象中建立 ndarray 对象，返回一维数组。

```text
numpy.fromiter(iterable, dtype, count=-1)
```


## 实例

```text
import numpy as np

# 使用 range 函数创建列表对象
list=range(5)
it=iter(list)

# 使用迭代器创建 ndarray
x=np.fromiter(it, dtype=float)
print(x)
```

输出结果为：

```text
[0. 1. 2. 3. 4.]
```


## 复习重点

- 能说明 `NumPy 从已有的数组创建数组` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
