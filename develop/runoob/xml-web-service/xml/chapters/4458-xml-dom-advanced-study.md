# XML：XML DOM 高级

- 来源：[XML DOM 高级](https://www.runoob.com/xml/xml-dom-advanced.html)
- 分类：XML / Web Service
- 技术：XML
- 笔记类型：学习笔记
- 章节序号：4458

## 本章内容

## XML DOM - 高级

在本教程的较早章节中，我们介绍了 XML DOM，并使用了 XML DOM 的 getElementsByTagName() 方法从 XML 文档中取回数据。

在本章中我们将结合一些其他重要的 XML DOM 方法。

您可以在我们的 XML DOM 教程 中学习更多有关 XML DOM 的知识。


## 获取元素的值

下面的实例中使用的 XML 文件：books.xml。

下面的实例检索第一个 <title> 元素的文本值：


## 实例


## 获取属性的值

下面的实例检索第一个 <title> 元素的 "lang" 属性的文本值：


## 实例


## 改变元素的值

下面的实例改变第一个 <title> 元素的文本值：


## 实例


## 创建新的属性

XML DOM 的 setAttribute() 方法可用于改变现有的属性值，或创建一个新的属性。

下面的实例创建了一个新的属性（edition="first"），然后把它添加到每一个 <book> 元素中：


## 实例


## 创建元素

XML DOM 的 createElement() 方法创建一个新的元素节点。

XML DOM 的 createTextNode() 方法创建一个新的文本节点。

XML DOM 的 appendChild() 方法向节点添加子节点（在最后一个子节点之后）。

如需创建带有文本内容的新元素，需要同时创建元一个新的元素节点和一个新的文本节点，然后把他追加到现有的节点。

下面的实例创建了一个新的元素（<edition>），带有如下文本：First，然后把它添加到第一个 <book> 元素：


## 实例

实例解释

- 创建一个 <edition> 元素
- 创建值为 "First" 的文本节点
- 把这个文本节点追加到新的 <edition> 元素
- 把 <edition> 元素追加到第一个 <book> 元素


## 删除元素

下面的实例删除第一个 <book> 元素的第一个节点：


## 实例

注释：上面实例的结果可能会根据所用的浏览器而不同。Firefox 把新行字符当作空的文本节点，而 Internet Explorer 不是这样。您可以在我们的 XML DOM 教程 中阅读到更多有关这个问题以及如何避免它的知识。


## 复习重点

- 能说明 `XML DOM 高级` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
