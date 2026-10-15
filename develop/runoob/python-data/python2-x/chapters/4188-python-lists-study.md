# Python2.x：Python 列表(List)

- 来源：[Python 列表(List)](https://www.runoob.com/python/python-lists.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：学习笔记
- 章节序号：4188

## 本章内容

序列是Python中最基本的数据结构。序列中的每个元素都分配一个数字 - 它的位置，或索引，第一个索引是0，第二个索引是1，依此类推。

Python有6个序列的内置类型，但最常见的是列表和元组。

序列都可以进行的操作包括索引，切片，加，乘，检查成员。

此外，Python已经内置确定序列的长度以及确定最大和最小的元素的方法。

列表是最常用的Python数据类型，它可以作为一个方括号内的逗号分隔值出现。

列表的数据项不需要具有相同的类型

创建一个列表，只要把逗号分隔的不同的数据项使用方括号括起来即可。如下所示：

```text
list1 = ['physics', 'chemistry', 1997, 2000]
list2 = [1, 2, 3, 4, 5 ]
list3 = ["a", "b", "c", "d"]
```

与字符串的索引一样，列表索引从0开始。列表可以进行截取、组合等。


## 访问列表中的值

使用下标索引来访问列表中的值，同样你也可以使用方括号的形式截取字符，如下所示：


## 实例(Python 2.0+)

```java
#!/usr/bin/python

list1 = ['physics', 'chemistry', 1997, 2000]
list2 = [1, 2, 3, 4, 5, 6, 7 ]

print "list1[0]: ", list1[0]
print "list2[1:5]: ", list2[1:5]
```

以上实例输出结果：

```text
list1[0]:  physics
list2[1:5]:  [2, 3, 4, 5]
```


## 更新列表

你可以对列表的数据项进行修改或更新，你也可以使用append()方法来添加列表项，如下所示：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

list = []          ## 空列表
list.append('Google')   ## 使用 append() 添加元素
list.append('Runoob')
print list
```

注意：我们会在接下来的章节讨论append()方法的使用

以上实例输出结果：

```text
['Google', 'Runoob']
```


## 删除列表元素

可以使用 del 语句来删除列表的元素，如下实例：


## 实例(Python 2.0+)

```java
#!/usr/bin/python

list1 = ['physics', 'chemistry', 1997, 2000]

print list1
del list1[2]
print "After deleting value at index 2 : "
print list1
```

以上实例输出结果：

```text
['physics', 'chemistry', 1997, 2000]
After deleting value at index 2 :
['physics', 'chemistry', 2000]
```

注意：我们会在接下来的章节讨论remove()方法的使用


## Python列表脚本操作符

列表对 + 和 * 的操作符与字符串相似。+ 号用于组合列表，* 号用于重复列表。

如下所示：


## Python列表截取

Python 的列表截取实例如下：

```text
>>>L = ['Google', 'Runoob', 'Taobao']
>>> L[2]
'Taobao'
>>> L[-2]
'Runoob'
>>> L[1:]
['Runoob', 'Taobao']
>>>
```

描述：


## Python列表函数&方法

Python包含以下函数:

Python包含以下方法:


## 复习重点

- 能说明 `Python 列表(List)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
