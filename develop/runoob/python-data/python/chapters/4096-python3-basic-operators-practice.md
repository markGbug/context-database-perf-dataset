# Python：Python3 运算符

- 来源：[Python3 运算符](https://www.runoob.com/python3/python3-basic-operators.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4096

## 本章内容

## 什么是运算符？

本章节主要说明 Python 的运算符。

举个简单的例子:

```text
4 + 5 = 9
```

例子中，4 和 5 被称为操作数，+ 称为运算符。

Python 语言支持以下类型的运算符:

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

以下假设变量 a=10，变量 b=21：

```text
>>> 9//2
4
>>> -9//2
-5
```

以下实例演示了Python所有算术运算符的操作：


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

a = 21
b = 10
c = 0

c = a + b
print ("1 - c 的值为：", c)

c = a - b
print ("2 - c 的值为：", c)

c = a * b
print ("3 - c 的值为：", c)

c = a / b
print ("4 - c 的值为：", c)

c = a % b
print ("5 - c 的值为：", c)

# 修改变量 a 、b 、c
a = 2
b = 3
c = a**b
print ("6 - c 的值为：", c)

a = 10
b = 5
c = a//b
print ("7 - c 的值为：", c)
```

以上实例输出结果：

```text
1 - c 的值为： 31
2 - c 的值为： 11
3 - c 的值为： 210
4 - c 的值为： 2.1
5 - c 的值为： 1
6 - c 的值为： 8
7 - c 的值为： 2
```


## Python 比较运算符

以下假设变量 a 为 10，变量 b 为20：

以下实例演示了Python所有比较运算符的操作：


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

a = 21
b = 10
c = 0

if ( a == b ):
   print ("1 - a 等于 b")
else:
   print ("1 - a 不等于 b")

if ( a != b ):
   print ("2 - a 不等于 b")
else:
   print ("2 - a 等于 b")

if ( a < b ):
   print ("3 - a 小于 b")
else:
   print ("3 - a 大于等于 b")

if ( a > b ):
   print ("4 - a 大于 b")
else:
   print ("4 - a 小于等于 b")

# 修改变量 a 和 b 的值
a = 5
b = 20
if ( a <= b ):
   print ("5 - a 小于等于 b")
else:
   print ("5 - a 大于  b")

if ( b >= a ):
   print ("6 - b 大于等于 a")
else:
   print ("6 - b 小于 a")
```

以上实例输出结果：

```text
1 - a 不等于 b
2 - a 不等于 b
3 - a 大于等于 b
4 - a 大于 b
5 - a 小于等于 b
6 - b 大于等于 a
```


## Python赋值运算符

以下假设变量a为10，变量b为20：

在这个示例中，赋值表达式可以避免调用 len() 两次:

```text
if (n := len(a)) > 10:
    print(f"List is too long ({n} elements, expected <= 10)")
```

以下实例演示了Python所有赋值运算符的操作：


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

a = 21
b = 10
c = 0

c = a + b
print ("1 - c 的值为：", c)

c += a
print ("2 - c 的值为：", c)

c *= a
print ("3 - c 的值为：", c)

c /= a
print ("4 - c 的值为：", c)

c = 2
c %= a
print ("5 - c 的值为：", c)

c **= a
print ("6 - c 的值为：", c)

c //= a
print ("7 - c 的值为：", c)
```

以上实例输出结果：

```text
1 - c 的值为： 31
2 - c 的值为： 52
3 - c 的值为： 1092
4 - c 的值为： 52.0
5 - c 的值为： 2
6 - c 的值为： 2097152
7 - c 的值为： 99864
```

在 Python 3.8 及更高版本中，引入了一种新的语法特性，称为"海象运算符"（Walrus Operator），它使用 := 符号。这个运算符的主要目的是在表达式中同时进行赋值和返回赋值的值。

使用海象运算符可以在一些情况下简化代码，尤其是在需要在表达式中使用赋值结果的情况下。这对于简化循环条件或表达式中的重复计算很有用。

下面是一个简单的实例，演示了海象运算符的使用：


## 实例

- if (n := 10) > 5:：这是使用海象运算符（:=）的写法。海象运算符在表达式中进行赋值操作。(n := 10)：将变量 n 赋值为 10，同时返回这个赋值结果。> 5：检查赋值后的 n 是否大于 5。如果条件为真，则执行接下来的代码块。
- print(n)：如果条件为真，打印变量 n 的值（即 10）。

海象运算符的优点：

- 海象运算符（:=）允许在表达式内部进行赋值，这可以减少代码的重复，提高代码的可读性和简洁性。
- 在上述例子中，传统写法需要单独一行来赋值 n，然后在 if 语句中进行条件检查。而使用海象运算符的写法可以在 if 语句中直接进行赋值和条件检查。


## Python位运算符

按位运算符是把数字看作二进制来进行计算的。Python中的按位运算法则如下：

下表中变量 a 为 60，b 为 13二进制格式如下：

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


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

a = 60            # 60 = 0011 1100
b = 13            # 13 = 0000 1101
c = 0

c = a & b        # 12 = 0000 1100
print ("1 - c 的值为：", c)

c = a | b        # 61 = 0011 1101
print ("2 - c 的值为：", c)

c = a ^ b        # 49 = 0011 0001
print ("3 - c 的值为：", c)

c = ~a           # -61 = 1100 0011
print ("4 - c 的值为：", c)

c = a << 2       # 240 = 1111 0000
print ("5 - c 的值为：", c)

c = a >> 2       # 15 = 0000 1111
print ("6 - c 的值为：", c)
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


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

a = 10
b = 20

if ( a and b ):
   print ("1 - 变量 a 和 b 都为 true")
else:
   print ("1 - 变量 a 和 b 有一个不为 true")

if ( a or b ):
   print ("2 - 变量 a 和 b 都为 true，或其中一个变量为 true")
else:
   print ("2 - 变量 a 和 b 都不为 true")

# 修改变量 a 的值
a = 0
if ( a and b ):
   print ("3 - 变量 a 和 b 都为 true")
else:
   print ("3 - 变量 a 和 b 有一个不为 true")

if ( a or b ):
   print ("4 - 变量 a 和 b 都为 true，或其中一个变量为 true")
else:
   print ("4 - 变量 a 和 b 都不为 true")

if not( a and b ):
   print ("5 - 变量 a 和 b 都为 false，或其中一个变量为 false")
else:
   print ("5 - 变量 a 和 b 都为 true")
```

以上实例输出结果：

```text
1 - 变量 a 和 b 都为 true
2 - 变量 a 和 b 都为 true，或其中一个变量为 true
3 - 变量 a 和 b 有一个不为 true
4 - 变量 a 和 b 都为 true，或其中一个变量为 true
5 - 变量 a 和 b 都为 false，或其中一个变量为 false
```


## Python成员运算符

除了以上的一些运算符之外，Python还支持成员运算符，测试实例中包含了一系列的成员，包括字符串，列表或元组。

以下实例演示了Python所有成员运算符的操作：


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

a = 10
b = 20
list = [1, 2, 3, 4, 5 ]

if ( a in list ):
   print ("1 - 变量 a 在给定的列表中 list 中")
else:
   print ("1 - 变量 a 不在给定的列表中 list 中")

if ( b not in list ):
   print ("2 - 变量 b 不在给定的列表中 list 中")
else:
   print ("2 - 变量 b 在给定的列表中 list 中")

# 修改变量 a 的值
a = 2
if ( a in list ):
   print ("3 - 变量 a 在给定的列表中 list 中")
else:
   print ("3 - 变量 a 不在给定的列表中 list 中")
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


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

a = 20
b = 20

if ( a is b ):
   print ("1 - a 和 b 有相同的标识")
else:
   print ("1 - a 和 b 没有相同的标识")

if ( id(a) == id(b) ):
   print ("2 - a 和 b 有相同的标识")
else:
   print ("2 - a 和 b 没有相同的标识")

# 修改变量 b 的值
b = 30
if ( a is b ):
   print ("3 - a 和 b 有相同的标识")
else:
   print ("3 - a 和 b 没有相同的标识")

if ( a is not b ):
   print ("4 - a 和 b 没有相同的标识")
else:
   print ("4 - a 和 b 有相同的标识")
```

以上实例输出结果：

```text
1 - a 和 b 有相同的标识
2 - a 和 b 有相同的标识
3 - a 和 b 没有相同的标识
4 - a 和 b 没有相同的标识
```

is 与 == 区别：

is 用于判断两个变量引用对象是否为同一个， == 用于判断引用变量的值是否相等。

```text
>>>a = [1, 2, 3]
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

以下表格列出了从最高到最低优先级的所有运算符， 相同单元格内的运算符具有相同优先级。 运算符均指二元运算，除非特别指出。 相同单元格内的运算符从左至右分组（除了幂运算是从右至左分组）：

运算符

描述

(expressions...),

[expressions...], {key: value...}, {expressions...}

圆括号的表达式

x[index], x[index:index], x(arguments...), x.attribute

读取，切片，调用，属性引用

await x

await 表达式

**

乘方(指数)

+x, -x, ~x

正，负，按位非 NOT

*, @, /, //, %

乘，矩阵乘，除，整除，取余

+, -

加和减

<<, >>

移位

&

按位与 AND

^

按位异或 XOR

|

按位或 OR

in,not in, is,is not, <, <=, >, >=, !=, ==

比较运算，包括成员检测和标识号检测


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

a = 20
b = 10
c = 15
d = 5
e = 0

e = (a + b) * c / d       #( 30 * 15 ) / 5
print ("(a + b) * c / d 运算结果为：",  e)

e = ((a + b) * c) / d     # (30 * 15 ) / 5
print ("((a + b) * c) / d 运算结果为：",  e)

e = (a + b) * (c / d)    # (30) * (15/5)
print ("(a + b) * (c / d) 运算结果为：",  e)

e = a + (b * c) / d      #  20 + (150/5)
print ("a + (b * c) / d 运算结果为：",  e)
```

以上实例输出结果：

```text
(a + b) * c / d 运算结果为： 90.0
((a + b) * c) / d 运算结果为： 90.0
(a + b) * (c / d) 运算结果为： 90.0
a + (b * c) / d 运算结果为： 50.0
```

and 拥有更高优先级:


## 实例

```text
x = True
y = False
z = False

print("情况1：默认优先级（先算and）")
if x or y and z:  # 等同于 x or (y and z)
    print("yes")  # 会输出
else:
    print("no")

print("\n情况2：强制改变优先级（先算or）")
if (x or y) and z:  # 人为添加括号改变顺序
    print("yes")  # 不会输出
else:
    print("no")  # 会输出
```

以上实例先计算 y and z 并返回 False ，然后 x or False 返回 True，输出结果：

```text
情况1：默认优先级（先算and）
yes

情况2：强制改变优先级（先算or）
no
```

注意：Python3 已不支持 <> 运算符，可以使用 != 代替，如果你一定要使用这种比较运算符，可以使用以下的方式：

```text
>>> from __future__ import barry_as_FLUFL
>>> 1 <> 2
True
```

```text
x = True
y = False
z = False

if x or y and z:
    print("yes")
else:
    print("no")
```

```text
x = True
y = False
z = False

if not x or y:
    print(1)
elif not x or not y and z:
    print(2)
elif not x or y or not y and x:
    print(3)
else:
    print(4)
```

课后练习


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python3 运算符` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
