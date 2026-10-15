# NumPy：NumPy 从数值范围创建数组

- 来源：[NumPy 从数值范围创建数组](https://www.runoob.com/numpy/numpy-array-from-numerical-ranges.html)
- 分类：Python / 数据科学
- 技术：NumPy
- 笔记类型：练习笔记
- 章节序号：3985

## 本章内容

这一章节我们将学习如何从数值范围创建数组。


### numpy.arange

numpy 包中的使用 arange 函数创建数值范围并返回 ndarray 对象，函数格式如下：

```text
numpy.arange(start, stop, step, dtype)
```

根据 start 与 stop 指定的范围以及 step 设定的步长，生成一个 ndarray。

参数说明：


### 实例

生成 0 到 4 长度为 5 的数组:


## 实例

```java
import numpy as np

x = np.arange(5)
print (x)
```

输出结果如下：

```text
[0  1  2  3  4]
```

设置返回类型位 float:


## 实例

```java
import numpy as np

# 设置了 dtype
x = np.arange(5, dtype =  float)
print (x)
```

输出结果如下：

```text
[0.  1.  2.  3.  4.]
```

设置了起始值、终止值及步长：


## 实例

```java
import numpy as np
x = np.arange(10,20,2)
print (x)
```

输出结果如下：

```text
[10  12  14  16  18]
```


### numpy.linspace

numpy.linspace 函数用于创建一个一维数组，数组是一个等差数列构成的，格式如下：

```text
np.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None)
```

参数说明：

以下实例用到三个参数，设置起始点为 1 ，终止点为 10，数列个数为 10。


## 实例

```text
import numpy as np
a = np.linspace(1,10,10)
print(a)
```

输出结果为：

```text
[ 1.  2.  3.  4.  5.  6.  7.  8.  9. 10.]
```

设置元素全部是1的等差数列：


## 实例

```text
import numpy as np
a = np.linspace(1,1,10)
print(a)
```

输出结果为：

```text
[1. 1. 1. 1. 1. 1. 1. 1. 1. 1.]
```

将 endpoint 设为 false，不包含终止值：


## 实例

```java
import numpy as np

a = np.linspace(10, 20,  5, endpoint =  False)
print(a)
```

输出结果为：

```text
[10. 12. 14. 16. 18.]
```

如果将 endpoint 设为 true，则会包含 20。

以下实例设置间距。


## 实例

```text
import numpy as np
a =np.linspace(1,10,10,retstep= True)

print(a)
# 拓展例子
b =np.linspace(1,10,10).reshape([10,1])
print(b)
```

输出结果为：

```text
(array([ 1.,  2.,  3.,  4.,  5.,  6.,  7.,  8.,  9., 10.]), 1.0)
[[ 1.]
 [ 2.]
 [ 3.]
 [ 4.]
 [ 5.]
 [ 6.]
 [ 7.]
 [ 8.]
 [ 9.]
 [10.]]
```


### numpy.logspace

numpy.logspace 函数用于创建一个于等比数列。格式如下：

```text
np.logspace(start, stop, num=50, endpoint=True, base=10.0, dtype=None)
```

base 参数意思是取对数的时候 log 的下标。


## 实例

```java
import numpy as np
# 默认底数是 10
a = np.logspace(1.0,  2.0, num =  10)
print (a)
```

输出结果为：

```text
[ 10.           12.91549665     16.68100537      21.5443469  27.82559402
  35.93813664   46.41588834     59.94842503      77.42636827    100.    ]
```

将对数的底数设置为 2 :


## 实例

```java
import numpy as np
a = np.logspace(0,9,10,base=2)
print (a)
```

输出如下：

```text
[  1.   2.   4.   8.  16.  32.  64. 128. 256. 512.]
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `NumPy 从数值范围创建数组` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
