# Python2.x：Python 运算符

- 来源：[Python 运算符](https://www.runoob.com/python/python-operators.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：练习笔记
- 章节序号：4177

## 本章内容

## 什么是运算符？

本章节主要说明Python的运算符。举个简单的例子 4 +5 = 9 。 例子中，4 和 5 被称为操作数，+ 称为运算符。

Python语言支持以下类型的运算符:

- 算术运算符
- 比较（关系）运算符
- 赋值运算符
- 逻辑运算符
- 位运算符
- 成员运算符
- 身份运算符
- 运算符优先级

接下来让我们一个个来学习Python的运算符。


## Python算术运算符

以下假设变量： a=10，b=20：

```text
>>> 9//2
4
>>> -9//2
-5
```

以下实例演示了Python所有算术运算符的操作：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

a = 21
b = 10
c = 0

c = a + b
print "1 - c 的值为：", c

c = a - b
print "2 - c 的值为：", c

c = a * b
print "3 - c 的值为：", c

c = a / b
print "4 - c 的值为：", c

c = a % b
print "5 - c 的值为：", c

# 修改变量 a 、b 、c
a = 2
b = 3
c = a**b
print "6 - c 的值为：", c

a = 10
b = 5
c = a//b
print "7 - c 的值为：", c
```

以上实例输出结果：

```text
1 - c 的值为： 31
2 - c 的值为： 11
3 - c 的值为： 210
4 - c 的值为： 2
5 - c 的值为： 1
6 - c 的值为： 8
7 - c 的值为： 2
```

注意：Python2.x 里，整数除整数，只能得出整数。如果要得到小数部分，把其中一个数改成浮点数即可。

```text
>>> 1/2
0
>>> 1.0/2
0.5
>>> 1/float(2)
0.5
```


## Python比较运算符

以下假设变量a为10，变量b为20：

以下实例演示了Python所有比较运算符的操作：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

a = 21
b = 10
c = 0

if  a == b :
   print "1 - a 等于 b"
else:
   print "1 - a 不等于 b"

if  a != b :
   print "2 - a 不等于 b"
else:
   print "2 - a 等于 b"

if  a <> b :
   print "3 - a 不等于 b"
else:
   print "3 - a 等于 b"

if  a < b :
   print "4 - a 小于 b"
else:
   print "4 - a 大于等于 b"

if  a > b :
   print "5 - a 大于 b"
else:
   print "5 - a 小于等于 b"

# 修改变量 a 和 b 的值
a = 5
b = 20
if  a <= b :
   print "6 - a 小于等于 b"
else:
   print "6 - a 大于  b"

if  b >= a :
   print "7 - b 大于等于 a"
else:
   print "7 - b 小于 a"
```

以上实例输出结果：

```text
1 - a 不等于 b
2 - a 不等于 b
3 - a 不等于 b
4 - a 大于等于 b
5 - a 大于 b
6 - a 小于等于 b
7 - b 大于等于 a
```


## Python赋值运算符

以下假设变量a为10，变量b为20：

以下实例演示了Python所有赋值运算符的操作：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

a = 21
b = 10
c = 0

c = a + b
print "1 - c 的值为：", c

c += a
print "2 - c 的值为：", c

c *= a
print "3 - c 的值为：", c

c /= a
print "4 - c 的值为：", c

c = 2
c %= a
print "5 - c 的值为：", c

c **= a
print "6 - c 的值为：", c

c //= a
print "7 - c 的值为：", c
```

以上实例输出结果：

```text
1 - c 的值为： 31
2 - c 的值为： 52
3 - c 的值为： 1092
4 - c 的值为： 52
5 - c 的值为： 2
6 - c 的值为： 2097152
7 - c 的值为： 99864
```


## Python位运算符

按位运算符是把数字看作二进制来进行计算的。Python中的按位运算法则如下：

下表中变量 a 为 60，b 为 13，二进制格式如下：

```text
a = 0011 1100

b = 0000 1101

-----------------

a&b = 0000 1100

a|b = 0011 1101

a^b = 0011 0001

~a  = 1100 0011
```

以下实例演示了Python所有位运算符的操作：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

a = 60            # 60 = 0011 1100
b = 13            # 13 = 0000 1101
c = 0

c = a & b;        # 12 = 0000 1100
print "1 - c 的值为：", c

c = a | b;        # 61 = 0011 1101
print "2 - c 的值为：", c

c = a ^ b;        # 49 = 0011 0001
print "3 - c 的值为：", c

c = ~a;           # -61 = 1100 0011
print "4 - c 的值为：", c

c = a << 2;       # 240 = 1111 0000
print "5 - c 的值为：", c

c = a >> 2;       # 15 = 0000 1111
print "6 - c 的值为：", c
```

以上实例输出结果：

```text
1 - c 的值为： 12
2 - c 的值为： 61
3 - c 的值为： 49
4 - c 的值为： -61
5 - c 的值为： 240
6 - c 的值为： 15
```


## Python逻辑运算符

Python语言支持逻辑运算符，以下假设变量 a 为 10, b为 20:

以上实例输出结果：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

a = 10
b = 20

if  a and b :
   print "1 - 变量 a 和 b 都为 True"
else:
   print "1 - 变量 a 和 b 有一个不为 True"

if  a or b :
   print "2 - 变量 a 和 b 都为 True，或其中一个变量为 True"
else:
   print "2 - 变量 a 和 b 都不为 True"

# 修改变量 a 的值
a = 0
if  a and b :
   print "3 - 变量 a 和 b 都为 True"
else:
   print "3 - 变量 a 和 b 有一个不为 True"

if  a or b :
   print "4 - 变量 a 和 b 都为 True，或其中一个变量为 True"
else:
   print "4 - 变量 a 和 b 都不为 True"

if not( a and b ):
   print "5 - 变量 a 和 b 都为 False，或其中一个变量为 False"
else:
   print "5 - 变量 a 和 b 都为 True"
```

以上实例输出结果：

```text
1 - 变量 a 和 b 都为 True
2 - 变量 a 和 b 都为 True，或其中一个变量为 True
3 - 变量 a 和 b 有一个不为 True
4 - 变量 a 和 b 都为 True，或其中一个变量为 True
5 - 变量 a 和 b 都为 False，或其中一个变量为 False
```


## Python成员运算符

除了以上的一些运算符之外，Python还支持成员运算符，测试实例中包含了一系列的成员，包括字符串，列表或元组。

以下实例演示了Python所有成员运算符的操作：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

a = 10
b = 20
list = [1, 2, 3, 4, 5 ];

if ( a in list ):
   print "1 - 变量 a 在给定的列表中 list 中"
else:
   print "1 - 变量 a 不在给定的列表中 list 中"

if ( b not in list ):
   print "2 - 变量 b 不在给定的列表中 list 中"
else:
   print "2 - 变量 b 在给定的列表中 list 中"

# 修改变量 a 的值
a = 2
if ( a in list ):
   print "3 - 变量 a 在给定的列表中 list 中"
else:
   print "3 - 变量 a 不在给定的列表中 list 中"
```

以上实例输出结果：

```text
1 - 变量 a 不在给定的列表中 list 中
2 - 变量 b 不在给定的列表中 list 中
3 - 变量 a 在给定的列表中 list 中
```


## Python身份运算符

身份运算符用于比较两个对象的存储单元

注： id() 函数用于获取对象内存地址。

以下实例演示了Python所有身份运算符的操作：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

a = 20
b = 20

if ( a is b ):
   print "1 - a 和 b 有相同的标识"
else:
   print "1 - a 和 b 没有相同的标识"

if ( a is not b ):
   print "2 - a 和 b 没有相同的标识"
else:
   print "2 - a 和 b 有相同的标识"

# 修改变量 b 的值
b = 30
if ( a is b ):
   print "3 - a 和 b 有相同的标识"
else:
   print "3 - a 和 b 没有相同的标识"

if ( a is not b ):
   print "4 - a 和 b 没有相同的标识"
else:
   print "4 - a 和 b 有相同的标识"
```

以上实例输出结果：

```text
1 - a 和 b 有相同的标识
2 - a 和 b 有相同的标识
3 - a 和 b 没有相同的标识
4 - a 和 b 没有相同的标识
```

is 与 == 区别：

is 用于判断两个变量引用对象是否为同一个(同一块内存空间)， == 用于判断引用变量的值是否相等。

```text
>>> a = [1, 2, 3]
>>> b = a
>>> b is a
True
>>> b == a
True
>>> b = a[:]
>>> b is a
False
>>> b == a
True
```


## Python运算符优先级

以下表格列出了从最高到最低优先级的所有运算符：

以下实例演示了Python所有运算符优先级的操作：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

a = 20
b = 10
c = 15
d = 5
e = 0

e = (a + b) * c / d       #( 30 * 15 ) / 5
print "(a + b) * c / d 运算结果为：",  e

e = ((a + b) * c) / d     # (30 * 15 ) / 5
print "((a + b) * c) / d 运算结果为：",  e

e = (a + b) * (c / d);    # (30) * (15/5)
print "(a + b) * (c / d) 运算结果为：",  e

e = a + (b * c) / d;      #  20 + (150/5)
print "a + (b * c) / d 运算结果为：",  e
```

以上实例输出结果：

```text
(a + b) * c / d 运算结果为： 90
((a + b) * c) / d 运算结果为： 90
(a + b) * (c / d) 运算结果为： 90
a + (b * c) / d 运算结果为： 50
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python 运算符` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
