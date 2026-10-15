# Python2.x：Python 字典(Dictionary)

- 来源：[Python 字典(Dictionary)](https://www.runoob.com/python/python-dictionary.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：练习笔记
- 章节序号：4190

## 本章内容

字典是另一种可变容器模型，且可存储任意类型对象。

字典的每个键值 key:value 对用冒号 : 分割，每个键值对之间用逗号 , 分割，整个字典包括在花括号 {} 中 ,格式如下所示：

```text
d = {key1 : value1, key2 : value2 }
```

注意：dict 作为 Python 的关键字和内置函数，变量名不建议命名为 dict。

键一般是唯一的，如果重复最后的一个键值对会替换前面的，值不需要唯一。

值可以取任何数据类型，但键必须是不可变的，如字符串，数字或元组。

一个简单的字典实例：

```text
tinydict = {'Alice': '2341', 'Beth': '9102', 'Cecil': '3258'}
```

也可如此创建字典：

```text
tinydict1 = { 'abc': 456 }
tinydict2 = { 'abc': 123, 98.6: 37 }
```


## 访问字典里的值

把相应的键放入熟悉的方括弧，如下实例:


## 实例

```java
#!/usr/bin/python

tinydict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}

print "tinydict['Name']: ", tinydict['Name']
print "tinydict['Age']: ", tinydict['Age']
```

以上实例输出结果：

```text
tinydict['Name']:  Zara
tinydict['Age']:  7
```

如果用字典里没有的键访问数据，会输出错误如下：


## 实例

```java
#!/usr/bin/python

tinydict = {'Name': 'Runoob', 'Age': 7, 'Class': 'First'}

print "tinydict['Alice']: ", tinydict['Alice']
```

以上实例输出结果：

```java
tinydict['Alice']:
Traceback (most recent call last):
  File "test.py", line 5, in <module>
    print "tinydict['Alice']: ", tinydict['Alice']
KeyError: 'Alice'
```


## 修改字典

向字典添加新内容的方法是增加新的键/值对，修改或删除已有键/值对如下实例:


## 实例

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

tinydict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}

tinydict['Age'] = 8 # 更新
tinydict['School'] = "RUNOOB" # 添加


print "tinydict['Age']: ", tinydict['Age']
print "tinydict['School']: ", tinydict['School']
```

```text
tinydict['Age']:  8
tinydict['School']:  RUNOOB
```


## 删除字典元素

能删单一的元素也能清空字典，清空只需一项操作。

显示删除一个字典用del命令，如下实例：


## 实例

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

tinydict = {'Name': 'Zara', 'Age': 7, 'Class': 'First'}

del tinydict['Name']  # 删除键是'Name'的条目
tinydict.clear()      # 清空字典所有条目
del tinydict          # 删除字典

print "tinydict['Age']: ", tinydict['Age']
print "tinydict['School']: ", tinydict['School']
```

但这会引发一个异常，因为用del后字典不再存在：

```java
tinydict['Age']:
Traceback (most recent call last):
  File "test.py", line 10, in <module>
    print "tinydict['Age']: ", tinydict['Age']
NameError: name 'tinydict' is not defined
```

注：del() 方法后面也会讨论。


### 字典键的特性

字典值可以没有限制地取任何 python 对象，既可以是标准的对象，也可以是用户定义的，但键不行。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python 字典(Dictionary)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
