# JavaScript：HTML DOM Document 对象

- 来源：[HTML DOM 对象](https://www.runoob.com/jsref/dom-obj-document.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2839

## 本章内容

## HTML DOM 节点

在 HTML DOM (Document Object Model) 中 , 每一个元素都是 节点:

- 文档是一个文档节点。
- 所有的HTML元素都是元素节点。
- 所有 HTML 属性都是属性节点。
- 文本插入到 HTML 元素是文本节点。are text nodes。
- 注释是注释节点。


## Document 对象

当浏览器载入 HTML 文档, 它就会成为 Document 对象。

Document 对象是 HTML 文档的根节点。

Document 对象使我们可以从脚本中对 HTML 页面中的所有元素进行访问。

提示：Document 对象是 Window 对象的一部分，可通过 window.document 属性对其进行访问。


## 浏览器支持

所有主要浏览器都支持 Document 对象。


## Document 对象属性和方法

HTML文档中可以使用以下属性和方法:

返回对文档中所有 Applet 对象的引用。

注意: HTML5 已不支持 <applet> 元素。


## 警告 !!!

在 W3C DOM核心，文档对象 继承节点对象的所有属性和方法。

很多属性和方法在文档中是没有意义的。

HTML 文档对象可以避免使用这些节点对象和属性：


## 复习重点

- 能说明 `HTML DOM 对象` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
