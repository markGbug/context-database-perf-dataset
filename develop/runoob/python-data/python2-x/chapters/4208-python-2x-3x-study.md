# Python2.x：Python2.x 与 3​​.x 版本区别

- 来源：[Python2.x 与 3​​.x 版本区别](https://www.runoob.com/python/python-2x-3x.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：学习笔记
- 章节序号：4208

## 本章内容

Python 的 3​​.0 版本，常被称为 Python 3000，或简称 Py3k。相对于 Python 的早期版本，这是一个较大的升级。

为了不带入过多的累赘，Python 3.0 在设计的时候没有考虑向下相容。

许多针对早期 Python 版本设计的程式都无法在 Python 3.0 上正常执行。

为了照顾现有程式，Python 2.6 作为一个过渡版本，基本使用了 Python 2.x 的语法和库，同时考虑了向 Python 3.0 的迁移，允许使用部分 Python 3.0 的语法与函数。

新的 Python 程式建议使用 Python 3.0 版本的语法。

除非执行环境无法安装 Python 3.0 或者程式本身使用了不支援 Python 3.0 的第三方库。目前不支持 Python 3.0 的第三方库有 Twisted, py2exe, PIL等。

大多数第三方库都正在努力地相容 Python 3.0 版本。即使无法立即使用 Python 3.0，也建议编写相容 Python 3.0 版本的程式，然后使用 Python 2.6, Python 2.7 来执行。

Python 3.0 的变化主要在以下几个方面:


## print 函数

print 语句没有了，取而代之的是 print() 函数。 Python 2.6 与 Python 2.7 部分地支持这种形式的 print 语法。在 Python 2.6 与Python 2.7 里面，以下三种形式是等价的：

```java
print "fish"
print ("fish") # 注意print后面有个空格
print("fish") # print()不能带有任何其它参数
```

然而，Python 2.6 实际已经支持新的 print() 语法，实例如下：

```text
from __future__ import print_function
print("fish", "panda", sep=', ')
```

如果 Python2.x 版本想使用使用 Python3.x 的 print 函数，可以导入 __future__ 包，该包禁用 Python2.x 的 print 语句，采用 Python3.x 的 print 函数：


## 实例

Python3.x 与 Python2.x 的许多兼容性设计的功能可以通过 __future__ 这个包来导入。


## Unicode

Python 2 有 ASCII str() 类型，unicode() 是单独的，不是 byte 类型。

现在， 在 Python 3，我们最终有了 Unicode (utf-8) 字符串，以及一个字节类：byte 和 bytearrays。

由于 Python3.x 源码文件默认使用 utf-8 编码，所以使用中文就更加方便了：

```text
>>> 中国 = 'china'
>>>print(中国)
china
```

Python 2.x

```text
>>> str = "我爱北京天安门"
>>> str
'\xe6\x88\x91\xe7\x88\xb1\xe5\x8c\x97\xe4\xba\xac\xe5\xa4\xa9\xe5\xae\x89\xe9\x97\xa8'
>>> str = u"我爱北京天安门"
>>> str
u'\u6211\u7231\u5317\u4eac\u5929\u5b89\u95e8'
```

Python 3.x

```text
>>> str = "我爱北京天安门"
>>> str
'我爱北京天安门'
```


## 除法运算

Python 中的除法较其它语言显得非常高端，有套很复杂的规则。Python 中的除法有两个运算符，/ 和 //

首先来说 / 除法:

在 Python 2.x 中 / 除法就跟我们熟悉的大多数语言，比如 Java 和 C ，整数相除的结果是一个整数，把小数部分完全忽略掉，浮点数除法会保留小数点的部分得到一个浮点数的结果。

在 Python 3.x 中 / 除法不再这么做了，对于整数之间的相除，结果也会是浮点数。

Python 2.x:

```text
>>> 1 / 2
0
>>> 1.0 / 2.0
0.5
```

Python 3.x:

```text
>>> 1/2
0.5
```

而对于 // 除法，这种除法叫做 floor 除法，会对除法的结果自动进行一个 floor 操作，在 Python 2.x 和 Python 3.x 中是一致的。

python 2.x:

```text
>>> -1 // 2
-1
```

python 3.x:

```text
>>> -1 // 2
-1
```

注意的是并不是舍弃小数部分，而是执行 floor 操作，如果要截取整数部分，那么需要使用 math 模块的 trunc 函数

python 3.x:

```text
>>> import math
>>> math.trunc(1 / 2)
0
>>> math.trunc(-1 / 2)
0
```


## 异常

在 Python 3 中处理异常也轻微的改变了，在 Python 3 中我们现在使用 as 作为关键词。

捕获异常的语法由 except exc, var 改为 except exc as var。

使用语法except (exc1, exc2) as var 可以同时捕获多种类别的异常。 Python 2.6 已经支持这两种语法。

- 1. 在 2.x 时代，所有类型的对象都是可以被直接抛出的，在 3.x 时代，只有继承自BaseException的对象才可以被抛出。
- 2. 2.x raise 语句使用逗号将抛出对象类型和参数分开，3.x 取消了这种奇葩的写法，直接调用构造函数抛出对象即可。


## 复习重点

- 能说明 `Python2.x 与 3​​.x 版本区别` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
