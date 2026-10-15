# Python：Python3 元组

- 来源：[Python3 元组](https://www.runoob.com/python3/python3-tuple.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：练习笔记
- 章节序号：4100

## 本章内容

Python 的元组与列表类似，不同之处在于元组的元素不能修改。

元组使用小括号 ( )，列表使用方括号 [ ]。

元组创建很简单，只需要在括号中添加元素，并使用逗号隔开即可。


## 实例(Python 3.0+)

创建空元组

```text
tup1 = ()
```

元组中只包含一个元素时，需要在元素后面添加逗号 , ，否则括号会被当作运算符使用：


## 实例(Python 3.0+)

元组与字符串类似，下标索引从 0 开始，可以进行截取，组合等。


## 访问元组

元组可以使用下标索引来访问元组中的值，如下实例:


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

tup1 = ('Google', 'Runoob', 1997, 2000)
tup2 = (1, 2, 3, 4, 5, 6, 7 )

print ("tup1[0]: ", tup1[0])
print ("tup2[1:5]: ", tup2[1:5])
```

以上实例输出结果：

```text
tup1[0]:  Google
tup2[1:5]:  (2, 3, 4, 5)
```


## 修改元组

元组中的元素值是不允许修改的，但我们可以对元组进行连接组合，如下实例:


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

tup1 = (12, 34.56)
tup2 = ('abc', 'xyz')

# 以下修改元组元素操作是非法的。
# tup1[0] = 100

# 创建一个新的元组
tup3 = tup1 + tup2
print (tup3)
```

以上实例输出结果：

```text
(12, 34.56, 'abc', 'xyz')
```


## 删除元组

元组中的元素值是不允许删除的，但我们可以使用del语句来删除整个元组，如下实例:


## 实例(Python 3.0+)

```java
#!/usr/bin/python3

tup = ('Google', 'Runoob', 1997, 2000)

print (tup)
del tup
print ("删除后的元组 tup : ")
print (tup)
```

以上实例元组被删除后，输出变量会有异常信息，输出如下所示：

```java
删除后的元组 tup :
Traceback (most recent call last):
  File "test.py", line 8, in <module>
    print (tup)
NameError: name 'tup' is not defined
```


## 元组运算符

与字符串一样，元组之间可以使用 +、+=和 * 号进行运算。这就意味着他们可以组合和复制，运算后会生成一个新的元组。

```text
len((1, 2, 3))
```

```text
>>> a = (1, 2, 3)
>>> b = (4, 5, 6)
>>> c = a+b
>>> c
(1, 2, 3, 4, 5, 6)
```

```text
>>> a = (1, 2, 3)
>>> b = (4, 5, 6)
>>> a += b
>>> a
(1, 2, 3, 4, 5, 6)
```

```text
('Hi!',) * 4
```

```text
3 in (1, 2, 3)
```

```java
for x in (1, 2, 3):
    print (x, end=" ")
```


## 元组索引，截取

因为元组也是一个序列，所以我们可以访问元组中的指定位置的元素，也可以截取索引中的一段元素，如下所示：

元组：

```text
tup = ('Google', 'Runoob', 'Taobao', 'Wiki', 'Weibo','Weixin')
```

运行实例如下：


## 实例


## 元组内置函数

Python元组包含了以下内置函数

```text
>>> tuple1 = ('Google', 'Runoob', 'Taobao')
>>> len(tuple1)
3
>>>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python3 元组` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
