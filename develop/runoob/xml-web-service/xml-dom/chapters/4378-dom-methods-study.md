# XML DOM：XML DOM - 属性和方法

- 来源：[DOM 方法](https://www.runoob.com/dom/dom-methods.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4378

## 本章内容

属性和方法向 XML DOM 定义了编程接口。


## 编程接口

DOM 把 XML 模拟为一系列节点对象。可通过 JavaScript 或其他编程语言来访问节点。在本教程中，我们使用 JavaScript。

对 DOM 的编程接口是通过一套标准的属性和方法来定义的。

属性经常按照"某事物是什么"的方式来使用（例如节点名是 "book"）。

方法经常按照"对某事物做什么"的方式来使用（例如删除 "book" 节点）。


## XML DOM 属性

一些典型的 DOM 属性：

- x.nodeName - x 的名称
- x.nodeValue - x 的值
- x.parentNode - x 的父节点
- x.childNodes - x 的子节点
- x.attributes - x 的属性节点

注释：在上面的列表中，x 是一个节点对象。


## XML DOM 方法

- x.getElementsByTagName(name) - 获取带有指定标签名称的所有元素
- x.appendChild(node) - 向 x 插入子节点
- x.removeChild(node) - 从 x 删除子节点

注释：在上面的列表中，x 是一个节点对象。


## 实例

从 books.xml 中的 <title> 元素获取文本的 JavaScript 代码：

txt=xmlDoc.getElementsByTagName("title")[0].childNodes[0].nodeValue

在该语句执行后，txt 保存的值是 "Everyday Italian"。

解释：

- xmlDoc - 由解析器创建的 XML DOM 对象
- getElementsByTagName("title")[0] - 第一个 <title> 元素
- childNodes[0] - <title> 元素的第一个子节点（文本节点）
- nodeValue - 节点的值（文本本身）


## 复习重点

- 能说明 `DOM 方法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
