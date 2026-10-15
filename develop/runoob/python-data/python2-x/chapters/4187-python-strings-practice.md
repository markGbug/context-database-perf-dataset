# Python2.x：Python 字符串

- 来源：[Python 字符串](https://www.runoob.com/python/python-strings.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：练习笔记
- 章节序号：4187

## 本章内容

字符串是 Python 中最常用的数据类型。我们可以使用引号 ( ' 或 " ) 来创建字符串。

创建字符串很简单，只要为变量分配一个值即可。例如：

```text
var1 = 'Hello World!'
var2 = "Python Runoob"
```


## Python 访问字符串中的值

Python 不支持单字符类型，单字符在 Python 中也是作为一个字符串使用。

Python 访问子字符串，可以使用方括号来截取字符串，如下实例：


## 实例(Python 2.0+)

```java
#!/usr/bin/python

var1 = 'Hello World!'
var2 = "Python Runoob"

print "var1[0]: ", var1[0]
print "var2[1:5]: ", var2[1:5]
```

以上实例执行结果：

```text
var1[0]:  H
var2[1:5]:  ytho
```


## Python 字符串连接

我们可以对字符串进行截取并与其他字符串进行连接，如下实例：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

var1 = 'Hello World!'

print "输出 :- ", var1[:6] + 'Runoob!'
```

以上实例执行结果

```text
输出 :-  Hello Runoob!
```


## Python 转义字符

在需要在字符中使用特殊字符时，python 用反斜杠 \ 转义字符。如下表：


## Python字符串运算符

下表实例变量 a 值为字符串 "Hello"，b 变量值为 "Python"：

```text
>>>a + b
'HelloPython'
```

```text
>>>a * 2
'HelloHello'
```

```text
>>>a[1]
'e'
```

```text
>>>a[1:4]
'ell'
```

```text
>>>"H" in a
True
```

```text
>>>"M" not in a
True
```

```java
>>>print r'\n'
\n
>>> print R'\n'
\n
```


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

a = "Hello"
b = "Python"

print "a + b 输出结果：", a + b
print "a * 2 输出结果：", a * 2
print "a[1] 输出结果：", a[1]
print "a[1:4] 输出结果：", a[1:4]

if( "H" in a) :
    print "H 在变量 a 中"
else :
    print "H 不在变量 a 中"

if( "M" not in a) :
    print "M 不在变量 a 中"
else :
    print "M 在变量 a 中"

print r'\n'
print R'\n'
```

以上程序执行结果为：

```text
a + b 输出结果： HelloPython
a * 2 输出结果： HelloHello
a[1] 输出结果： e
a[1:4] 输出结果： ell
H 在变量 a 中
M 不在变量 a 中
\n
\n
```


## Python 字符串格式化

Python 支持格式化字符串的输出 。尽管这样可能会用到非常复杂的表达式，但最基本的用法是将一个值插入到一个有字符串格式符 %s 的字符串中。

在 Python 中，字符串格式化使用与 C 中 sprintf 函数一样的语法。

如下实例：

```java
#!/usr/bin/python

print "My name is %s and weight is %d kg!" % ('Zara', 21)
```

以上实例输出结果：

```text
My name is Zara and weight is 21 kg!
```

python 字符串格式化符号:

格式化操作符辅助指令:

Python2.6 开始，新增了一种格式化字符串的函数 str.format()，它增强了字符串格式化的功能。


## Python 三引号

Python 中三引号可以将复杂的字符串进行赋值。

Python 三引号允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符。

三引号的语法是一对连续的单引号或者双引号（通常都是成对的用）。

```java
 >>> hi = '''hi
there'''
>>> hi   # repr()
'hi\nthere'
>>> print hi  # str()
hi
there
```

三引号让程序员从引号和特殊字符串的泥潭里面解脱出来，自始至终保持一小块字符串的格式是所谓的WYSIWYG（所见即所得）格式的。

一个典型的用例是，当你需要一块HTML或者SQL时，这时当用三引号标记，使用传统的转义字符体系将十分费神。

```html
 errHTML = '''
<HTML><HEAD><TITLE>
Friends CGI Demo</TITLE></HEAD>
<BODY><H3>ERROR</H3>
<B>%s</B><P>
<FORM><INPUT TYPE=button VALUE=Back
ONCLICK="window.history.back()"></FORM>
</BODY></HTML>
'''
cursor.execute('''
CREATE TABLE users (
login VARCHAR(8),
uid INTEGER,
prid INTEGER)
''')
```


## Unicode 字符串

Python 中定义一个 Unicode 字符串和定义一个普通字符串一样简单：

```text
>>> u'Hello World !'
u'Hello World !'
```

引号前小写的"u"表示这里创建的是一个 Unicode 字符串。如果你想加入一个特殊字符，可以使用 Python 的 Unicode-Escape 编码。如下例所示：

```text
>>> u'Hello\u0020World !'
u'Hello World !'
```

被替换的 \u0020 标识表示在给定位置插入编码值为 0x0020 的 Unicode 字符（空格符）。


## Python 的字符串内建函数

字符串方法是从 Python1.6 到 2.0 慢慢加进来的 —— 它们也被加到了Jython 中。

这些方法实现了 string 模块的大部分方法，如下表所示列出了目前字符串内建支持的方法，所有的方法都包含了对 Unicode 的支持，有一些甚至是专门用于 Unicode 的。

string.capitalize()

把字符串的第一个字符大写

string.center(width)

返回一个原字符串居中,并使用空格填充至长度 width 的新字符串

string.count(str, beg=0, end=len(string))

返回 str 在 string 里面出现的次数，如果 beg 或者 end 指定则返回指定范围内 str 出现的次数

string.decode(encoding='UTF-8', errors='strict')

以 encoding 指定的编码格式解码 string，如果出错默认报一个 ValueError 的 异 常 ， 除非 errors 指 定 的 是 'ignore' 或 者'replace'

string.encode(encoding='UTF-8', errors='strict')

以 encoding 指定的编码格式编码 string，如果出错默认报一个ValueError 的异常，除非 errors 指定的是'ignore'或者'replace'

string.endswith(obj, beg=0, end=len(string))

检查字符串是否以 obj 结束，如果beg 或者 end 指定则检查指定的范围内是否以 obj 结束，如果是，返回 True,否则返回 False.

string.expandtabs(tabsize=8)

把字符串 string 中的 tab 符号转为空格，tab 符号默认的空格数是 8。

string.find(str, beg=0, end=len(string))

检测 str 是否包含在 string 中，如果 beg 和 end 指定范围，则检查是否包含在指定范围内，如果是返回开始的索引值，否则返回-1

string.format()

格式化字符串

string.index(str, beg=0, end=len(string))

跟find()方法一样，只不过如果str不在 string中会报一个异常.

string.isalnum()

如果 string 至少有一个字符并且所有字符都是字母或数字则返

回 True,否则返回 False

string.isalpha()

如果 string 至少有一个字符并且所有字符都是字母则返回 True,

否则返回 False


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python 字符串` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
