# Python2.x：Python continue 语句

- 来源：[Python continue 语句](https://www.runoob.com/python/python-continue-statement.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：练习笔记
- 章节序号：4184

## 本章内容

Python continue 语句跳出本次循环，而break跳出整个循环。

continue 语句用来告诉Python跳过当前循环的剩余语句，然后继续进行下一轮循环。

continue语句用在while和for循环中。

Python 语言 continue 语句语法格式如下：

```text
continue
```

流程图：

实例：


## 实例(Python 2.0+)

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

for letter in 'Python':     # 第一个实例
   if letter == 'h':
      continue
   print '当前字母 :', letter

var = 10                    # 第二个实例
while var > 0:
   var = var -1
   if var == 5:
      continue
   print '当前变量值 :', var
print "Good bye!"
```

以上实例执行结果：

```text
当前字母 : P
当前字母 : y
当前字母 : t
当前字母 : o
当前字母 : n
当前变量值 : 9
当前变量值 : 8
当前变量值 : 7
当前变量值 : 6
当前变量值 : 4
当前变量值 : 3
当前变量值 : 2
当前变量值 : 1
当前变量值 : 0
Good bye!
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python continue 语句` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
