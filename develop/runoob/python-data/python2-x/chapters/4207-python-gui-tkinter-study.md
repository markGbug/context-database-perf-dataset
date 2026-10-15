# Python2.x：Python GUI编程(Tkinter)

- 来源：[Python GUI 编程(Tkinter)](https://www.runoob.com/python/python-gui-tkinter.html)
- 分类：Python / 数据科学
- 技术：Python2.x
- 笔记类型：学习笔记
- 章节序号：4207

## 本章内容

Python 提供了多个图形开发界面的库，几个常用 Python GUI 库如下：

- Tkinter： Tkinter 模块(Tk 接口)是 Python 的标准 Tk GUI 工具包的接口 .Tk 和 Tkinter 可以在大多数的 Unix 平台下使用,同样可以应用在 Windows 和 Macintosh 系统里。Tk8.0 的后续版本可以实现本地窗口风格,并良好地运行在绝大多数平台中。
- wxPython：wxPython 是一款开源软件，是 Python 语言的一套优秀的 GUI 图形库，允许 Python 程序员很方便的创建完整的、功能健全的 GUI 用户界面。
- Jython：Jython 程序可以和 Java 无缝集成。除了一些标准模块，Jython 使用 Java 的模块。Jython 几乎拥有标准的Python 中不依赖于 C 语言的全部模块。比如，Jython 的用户界面将使用 Swing，AWT或者 SWT。Jython 可以被动态或静态地编译成 Java 字节码。


## Tkinter 编程

Tkinter 是 Python 的标准 GUI 库。Python 使用 Tkinter 可以快速的创建 GUI 应用程序。

由于 Tkinter 是内置到 python 的安装包中、只要安装好 Python 之后就能 import Tkinter 库、而且 IDLE 也是用 Tkinter 编写而成、对于简单的图形界面 Tkinter 还是能应付自如。

注意：Python3.x 版本使用的库名为 tkinter,即首写字母 T 为小写。

```text
import tkinter
```

创建一个GUI程序

- 1、导入 Tkinter 模块
- 2、创建控件
- 3、指定这个控件的 master， 即这个控件属于哪一个
- 4、告诉 GM(geometry manager) 有一个控件产生了。


## 实例(Python3.x)

```text
#!/usr/bin/python3

import tkinter
top = tkinter.Tk()
# 进入消息循环
top.mainloop()
```


## 实例(Python2.x)

```text
#!/usr/bin/python
# -*- coding: UTF-8 -*-

import Tkinter
top = Tkinter.Tk()
# 进入消息循环
top.mainloop()
```

以上代码执行结果如下图:


## 实例

```text
#!/usr/bin/python
# -*- coding: UTF-8 -*-

# Python2.x 导入方法
from Tkinter import *           # 导入 Tkinter 库
# Python3.x 导入方法
#from tkinter import *
root = Tk()                     # 创建窗口对象的背景色
                                # 创建两个列表
li     = ['C','python','php','html','SQL','java']
movie  = ['CSS','jQuery','Bootstrap']
listb  = Listbox(root)          #  创建两个列表组件
listb2 = Listbox(root)
for item in li:                 # 第一个小部件插入数据
    listb.insert(0,item)

for item in movie:              # 第二个小部件插入数据
    listb2.insert(0,item)

listb.pack()                    # 将小部件放置到主窗口中
listb2.pack()
root.mainloop()                 # 进入消息循环
```

以上代码执行结果如下图:


## Tkinter 组件

Tkinter的提供各种控件，如按钮，标签和文本框，一个GUI应用程序中使用。这些控件通常被称为控件或者部件。

目前有15种Tkinter的部件。我们提出这些部件以及一个简短的介绍，在下面的表:


## 标准属性

标准属性也就是所有控件的共同属性，如大小，字体和颜色等等。


## 几何管理

Tkinter控件有特定的几何状态管理方法，管理整个控件区域组织，以下是Tkinter公开的几何管理类：包、网格、位置


## 复习重点

- 能说明 `Python GUI 编程(Tkinter)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
