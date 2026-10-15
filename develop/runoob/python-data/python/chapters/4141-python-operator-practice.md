# Python：Python3 operator 模块

- 来源：[Python3 operator](https://www.runoob.com/python3/python-operator.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4141

## 本章内容

Python2.x 版本中，使用 cmp() 函数来比较两个列表、数字或字符串等的大小关系。

Python 3.X 的版本中已经没有 cmp() 函数，如果你需要实现比较功能，需要引入 operator 模块，适合任何对象，包含的方法有：


## operator 模块包含的方法

operator.lt(a, b) 与 a < b 相同， operator.le(a, b) 与 a <= b 相同，operator.eq(a, b) 与 a == b 相同，operator.ne(a, b) 与 a != b 相同，operator.gt(a, b) 与 a > b 相同，operator.ge(a, b) 与 a >= b 相同。


## 实例

以上代码输出结果为：

```text
x: 10 , y: 20
operator.lt(x,y):  True
operator.gt(y,x):  True
operator.eq(x,x):  True
operator.ne(y,y):  False
operator.le(x,y):  True
operator.ge(y,x):  True

x: Google , y: Runoob
operator.lt(x,y):  True
operator.gt(y,x):  True
operator.eq(x,x):  True
operator.ne(y,y):  False
operator.le(x,y):  True
operator.ge(y,x):  True
```

比较两个列表：


## 实例

以上代码输出结果为：

```text
operator.eq(a,b):  False
operator.eq(c,b):  True
```


### 运算符函数

operator 模块提供了一套与 Python 的内置运算符对应的高效率函数。例如，operator.add(x, y) 与表达式 x+y 相同。

函数包含的种类有：对象的比较运算、逻辑运算、数学运算以及序列运算。

对象比较函数适用于所有的对象，函数名根据它们对应的比较运算符命名。

许多函数名与特殊方法名相同，只是没有双下划线。为了向后兼容性，也保留了许多包含双下划线的函数，为了表述清楚，建议使用没有双下划线的函数。


## 实例

以上代码输出结果为：

```text
add() 运算结果 :7
sub() 运算结果 :1
mul() 运算结果 :12
```

运算

语法

函数

加法

a + b

add(a, b)

字符串拼接

seq1 + seq2

concat(seq1, seq2)

包含测试

obj in seq

contains(seq, obj)

除法

a / b

truediv(a, b)

除法

a // b

floordiv(a, b)

按位与

a & b

and_(a, b)

按位异或

a ^ b

xor(a, b)

按位取反

~ a


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python3 operator` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
