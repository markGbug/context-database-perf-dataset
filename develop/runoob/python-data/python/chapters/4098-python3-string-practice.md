# Python：Python3 字符串

- 来源：[Python3 字符串](https://www.runoob.com/python3/python3-string.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4098

## 本章内容

字符串是 Python 中最常用的数据类型。我们可以使用引号( ' 或 " )来创建字符串。

创建字符串很简单，只要为变量分配一个值即可。例如：

```text
var1 = 'Hello World!'
var2 = "Runoob"
```


## Python 访问字符串中的值

Python 不支持单字符类型，单字符在 Python 中也是作为一个字符串使用。

Python 访问子字符串，可以使用方括号 [] 来截取字符串，字符串的截取的语法格式如下：

```text
变量[头下标:尾下标]
```

索引值以 0 为开始值，-1 为从末尾的开始位置。

如下实例：


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

var1 = 'Hello World!'
var2 = "Runoob"

print ("var1[0]: ", var1[0])
print ("var2[1:5]: ", var2[1:5])
```

以上实例执行结果：

```text
var1[0]:  H
var2[1:5]:  unoo
```


## Python 字符串更新

你可以截取字符串的一部分并与其他字段拼接，如下实例：


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

var1 = 'Hello World!'

print ("已更新字符串 : ", var1[:6] + 'Runoob!')
```

以上实例执行结果

```text
已更新字符串 :  Hello Runoob!
```


## Python 转义字符

在需要在字符中使用特殊字符时，python 用反斜杠 \ 转义字符。如下表：

```text
>>> print("line1 \
... line2 \
... line3")
line1 line2 line3
>>>
```

```text
>>> print("\\")
\
```

```text
>>> print('\'')
'
```

```text
>>> print("\"")
"
```

```text
>>> print("\a")
```

```text
>>> print("Hello \b World!")
Hello World!
```

```text
>>> print("\000")

>>>
```

```text
>>> print("\n")


>>>
```

```text
>>> print("Hello \v World!")
Hello
       World!
>>>
```

```text
>>> print("Hello \t World!")
Hello      World!
>>>
```

```text
>>> print("Hello\rWorld!")
World!
>>> print('google runoob taobao\r123456')
123456 runoob taobao
```

```text
>>> print("Hello \f World!")
Hello
       World!
>>>
```

```text
>>> print("\110\145\154\154\157\40\127\157\162\154\144\41")
Hello World!
```

```text
>>> print("\x48\x65\x6c\x6c\x6f\x20\x57\x6f\x72\x6c\x64\x21")
Hello World!
```

使用 \r 实现百分比进度：


## 实例

以下实例，我们使用了不同的转义字符来演示单引号、换行符、制表符、退格符、换页符、ASCII、二进制、八进制数和十六进制数的效果：


## 实例


## Python 字符串运算符

下表实例变量 a 值为字符串 "Hello"，b 变量值为 "Python"：

```text
print( r'\n' )
print( R'\n' )
```


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

a = "Hello"
b = "Python"

print("a + b 输出结果：", a + b)
print("a * 2 输出结果：", a * 2)
print("a[1] 输出结果：", a[1])
print("a[1:4] 输出结果：", a[1:4])

if( "H" in a) :
    print("H 在变量 a 中")
else :
    print("H 不在变量 a 中")

if( "M" not in a) :
    print("M 不在变量 a 中")
else :
    print("M 在变量 a 中")

print (r'\n')
print (R'\n')
```

以上实例输出结果为：

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


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

print ("我叫 %s 今年 %d 岁!" % ('小明', 10))
```

以上实例输出结果：

```text
我叫 小明 今年 10 岁!
```

python字符串格式化符号:

格式化操作符辅助指令:

Python2.6 开始，新增了一种格式化字符串的函数 str.format()，它增强了字符串格式化的功能。


## Python三引号

python三引号允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符。实例如下


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

para_str = """这是一个多行字符串的实例
多行字符串可以使用制表符
TAB ( \t )。
也可以使用换行符 [ \n ]。
"""
print (para_str)
```

以上实例执行结果为：

```text
这是一个多行字符串的实例
多行字符串可以使用制表符
TAB (    )。
也可以使用换行符 [
 ]。
```

三引号让程序员从引号和特殊字符串的泥潭里面解脱出来，自始至终保持一小块字符串的格式是所谓的WYSIWYG（所见即所得）格式的。

一个典型的用例是，当你需要一块HTML或者SQL时，这时用字符串组合，特殊字符串转义将会非常的繁琐。

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


## f-string

f-string 是 python3.6 之后版本添加的，称之为字面量格式化字符串，是新的格式化字符串的语法。

之前我们习惯用百分号 (%):


## 实例

f-string 格式化字符串以 f 开头，后面跟着字符串，字符串中的表达式用大括号 {} 包起来，它会将变量或表达式计算后的值替换进去，实例如下：


## 实例

用了这种方式明显更简单了，不用再去判断使用 %s，还是 %d。

在 Python 3.8 的版本中可以使用 = 符号来拼接运算表达式与结果：


## 实例


## Unicode 字符串

在Python2中，普通字符串是以8位ASCII码进行存储的，而Unicode字符串则存储为16位unicode字符串，这样能够表示更多的字符集。使用的语法是在字符串前面加上前缀 u。

在Python3中，所有的字符串都是Unicode字符串。


## Python 的字符串内建函数

Python 的字符串常用内建函数如下：

capitalize() 将字符串的第一个字符转换为大写

center(width, fillchar)

count(str, beg= 0,end=len(string))

bytes.decode(encoding="utf-8", errors="strict")

encode(encoding='UTF-8',errors='strict')

endswith(suffix, beg=0, end=len(string)) 检查字符串是否以 suffix 结束，如果 beg 或者 end 指定则检查指定的范围内是否以 suffix 结束，如果是，返回 True,否则返回 False。

expandtabs(tabsize=8)

find(str, beg=0, end=len(string))

index(str, beg=0, end=len(string))

isalnum()

isalpha()

isdigit()

islower()

isnumeric()

isspace()

istitle()

isupper()

join(seq)

len(string)

ljust(width[, fillchar])

lower()

lstrip()

maketrans()

max(str)

min(str)

replace(old, new [, max])

rfind(str, beg=0,end=len(string))


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python3 字符串` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
