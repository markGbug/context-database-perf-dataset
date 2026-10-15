# Python2.x：Python pass 语句

- 来源：[Python pass 语句](https://www.runoob.com/python/python-pass-statement.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：练习笔记
- 章节序号：4185

## 本章内容

Python pass 是空语句，是为了保持程序结构的完整性。

pass 不做任何事情，一般用做占位语句。

Python 语言 pass 语句语法格式如下：

```text
pass
```

测试实例：


## 实例

```java
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# 输出 Python 的每个字母
for letter in 'Python':
   if letter == 'h':
      pass
      print '这是 pass 块'
   print '当前字母 :', letter

print "Good bye!"
```

以上实例执行结果：

```text
当前字母 : P
当前字母 : y
当前字母 : t
这是 pass 块
当前字母 : h
当前字母 : o
当前字母 : n
Good bye!
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Python pass 语句` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
