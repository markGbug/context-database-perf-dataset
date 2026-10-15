# XML DOM：XML DOM 获取节点值

- 来源：[DOM 获取节点](https://www.runoob.com/dom/dom-nodes-get.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4385

## 本章内容

nodeValue 属性用于获取节点的文本值。

getAttribute() 方法返回属性的值。


## 获取元素的值

在 DOM 中，每种成分都是节点。元素节点没有文本值。

元素节点的文本存储在子节点中。该节点称为文本节点。

获取元素文本的方法，就是获取这个子节点（文本节点）的值。


## 获取元素值

getElementsByTagName() 方法返回包含拥有指定标签名的所有元素的节点列表，其中的元素的顺序是它们在源文档中出现的顺序。

下面的代码通过使用 loadXMLDoc() 把 books.xml 载入 xmlDoc 中并检索第一个 <title> 元素：

childNodes 属性返回子节点的列表。<title> 元素只有一个子节点。它是一个文本节点。

下面的代码检索 <title> 元素的文本节点：

nodeValue 属性返回文本节点的文本值：


## 实例

结果：txt = "Everyday Italian"

遍历所有 <title> 元素： 尝试一下


## 获取属性的值

在 DOM 中，属性也是节点。与元素节点不同，属性节点拥有文本值。

获取属性的值的方法，就是获取它的文本值。

可以通过使用 getAttribute() 方法或属性节点的 nodeValue 属性来完成这个任务。


## 获取属性值 - getAttribute()

getAttribute() 方法返回属性值。

下面的代码检索第一个 <title> 元素的 "lang" 属性的文本值：


## 实例

结果：txt = "en"

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 把 txt 变量设置为第一个 title 元素节点的 "lang" 属性的值

遍历所有的 <book> 元素，并获取它们的 "category" 属性： 尝试一下


## 获取属性值 - getAttributeNode()

getAttributeNode() 方法返回属性节点。

下面代码检索第一个 <title> 元素的 "lang" 属性的文本值：


## 实例

结果：Result: txt = "en"

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取第一个 <title> 元素节点的 "lang" 属性节点
- 把 txt 变量设置为属性的值

遍历所有的 <book> 元素并获取它们的 "category" 属性： 尝试一下


## 复习重点

- 能说明 `DOM 获取节点` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
