# Python：Python3 循环语句

- 来源：[Python3 循环语句](https://www.runoob.com/python3/python3-loop.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4104

## 本章内容

本章节将为大家介绍 Python 循环语句的使用。

Python 中的循环语句有 for 和 while。

Python 循环语句的控制结构图如下所示：


### 循环控制关键字与方法


## while 循环

Python 中 while 语句的一般形式：

```java
while 判断条件(condition)：
    执行语句(statements)……
```

执行流程图如下：

执行 Gif 演示：

同样需要注意冒号和缩进。另外，在 Python 中没有 do..while 循环。

以下实例使用了 while 来计算 1 到 100 的总和：


## 实例

```java
#!/usr/bin/env python3

n = 100

sum = 0
counter = 1
while counter <= n:
    sum = sum + counter
    counter += 1

print("1 到 %d 之和为: %d" % (n,sum))
```

执行结果如下：

```text
1 到 100 之和为: 5050
```


### 无限循环

我们可以通过设置条件表达式永远不为 false 来实现无限循环，实例如下：


## 实例

```java
#!/usr/bin/python3

var = 1
while var == 1 :  # 表达式永远为 true
   num = int(input("输入一个数字  :"))
   print ("你输入的数字是: ", num)

print ("Good bye!")
```

执行以上脚本，输出结果如下：

```text
输入一个数字  :5
你输入的数字是:  5
输入一个数字  :
```

你可以使用 CTRL+C 来退出当前的无限循环。

无限循环在服务器上客户端的实时请求非常有用。


### while 循环使用 else 语句

如果 while 后面的条件语句为 false 时，则执行 else 的语句块。

语法格式如下：

```java
while <expr>:
    <statement(s)>
else:
    <additional_statement(s)>
```

expr 条件语句为 true 则执行 statement(s) 语句块，如果为 false，则执行 additional_statement(s)。

循环输出数字，并判断大小：


## 实例

```java
#!/usr/bin/python3

count = 0
while count < 5:
   print (count, " 小于 5")
   count = count + 1
else:
   print (count, " 大于或等于 5")
```

执行以上脚本，输出结果如下：

```text
0  小于 5
1  小于 5
2  小于 5
3  小于 5
4  小于 5
5  大于或等于 5
```


### 简单语句组

类似 if 语句的语法，如果你的 while 循环体中只有一条语句，你可以将该语句与 while 写在同一行中， 如下所示：


## 实例

```java
#!/usr/bin/python

flag = 1

while (flag): print ('欢迎访问菜鸟教程!')

print ("Good bye!")
```

注意：以上的无限循环你可以使用 CTRL+C 来中断循环。

执行以上脚本，输出结果如下：

```text
欢迎访问菜鸟教程!
欢迎访问菜鸟教程!
欢迎访问菜鸟教程!
欢迎访问菜鸟教程!
欢迎访问菜鸟教程!
……
```


## for 语句

Python for 循环可以遍历任何可迭代对象，如一个列表或者一个字符串。

for循环的一般格式如下：

```html
for <variable> in <sequence>:
    <statements>
else:
    <statements>
```

流程图：

Python for 循环实例：


## 实例

```text
#!/usr/bin/python3

sites = ["Baidu", "Google","Runoob","Taobao"]
for site in sites:
    print(site)
```

以上代码执行输出结果为：

```text
Baidu
Google
Runoob
Taobao
```

也可用于打印字符串中的每个字符：


## 实例

```text
#!/usr/bin/python3

word = 'runoob'

for letter in word:
    print(letter)
```

以上代码执行输出结果为：

```text
r
u
n
o
o
b
```

整数范围值可以配合 range() 函数使用：


## 实例

```text
#!/usr/bin/python3

#  1 到 5 的所有数字：
for number in range(1, 6):
    print(number)
```

以上代码执行输出结果为：

```text
1
2
3
4
5
```


## for...else

在 Python 中，for...else 语句用于在循环结束后执行一段代码。

语法格式如下：

```text
for item in iterable:
    # 循环主体
else:
    # 循环结束后执行的代码
```

当循环执行完毕（即遍历完 iterable 中的所有元素）后，会执行 else 子句中的代码，如果在循环过程中遇到了 break 语句，则会中断循环，此时不会执行 else 子句。


## 实例

执行脚本后，输出结果为：

```text
0
1
2
3
4
5
Finally finished!
```

以下 for 实例中使用了 break 语句，break 语句用于跳出当前循环体，不会执行 else 子句：


## 实例

```text
#!/usr/bin/python3

sites = ["Baidu", "Google","Runoob","Taobao"]
for site in sites:
    if site == "Runoob":
        print("菜鸟教程!")
        break
    print("循环数据 " + site)
else:
    print("没有循环数据!")
print("完成循环!")
```

执行脚本后，在循环到 "Runoob"时会跳出循环体：

```text
循环数据 Baidu
循环数据 Google
菜鸟教程!
完成循环!
```


## range() 函数

如果你需要遍历数字序列，可以使用内置 range() 函数。它会生成数列，例如:


## 实例

```text
>>>for i in range(5):
...     print(i)
...
0
1
2
3
4
```

你也可以使用 range() 指定区间的值：


## 实例

```text
>>>for i in range(5,9) :
    print(i)


5
6
7
8
>>>
```

也可以使 range() 以指定数字开始并指定不同的增量(甚至可以是负数，有时这也叫做'步长'):


## 实例

```text
>>>for i in range(0, 10, 3) :
    print(i)


0
3
6
9
>>>
```

负数：


## 实例

```text
>>>for i in range(-10, -100, -30) :
    print(i)


-10
-40
-70
>>>
```

您可以结合 range() 和 len() 函数以遍历一个序列的索引,如下所示:


## 实例

```text
>>>a = ['Google', 'Baidu', 'Runoob', 'Taobao', 'QQ']
>>> for i in range(len(a)):
...     print(i, a[i])
...
0 Google
1 Baidu
2 Runoob
3 Taobao
4 QQ
>>>
```

还可以使用 range() 函数来创建一个列表：


## 实例

```text
>>>list(range(5))
[0, 1, 2, 3, 4]
>>>
```

更多关于 range() 函数用法参考：https://www.runoob.com/python3/python3-func-range.html


## break 和 continue 语句及循环中的 else 子句

break 执行流程图：

continue 执行流程图：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python3 循环语句` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
