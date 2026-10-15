# XML DOM：XML DOM 节点

- 来源：[DOM 节点](https://www.runoob.com/dom/dom-nodes.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4374

## 本章内容

在 DOM 中，XML 文档中的每个成分都是一个节点。


## DOM 节点

根据 DOM，XML 文档中的每个成分都是一个节点。

DOM 是这样规定的：

- 整个文档是一个文档节点
- 每个 XML 元素是一个元素节点
- 包含在 XML 元素中的文本是文本节点
- 每一个 XML 属性是一个属性节点
- 注释是注释节点


## DOM 实例

请看下面的 XML 文件（books.xml）：


## books.xml 文件代码：

```html
<?xml version="1.0" encoding="UTF-8"?>
<bookstore>
    <book category="cooking">
        <title lang="en">Everyday Italian</title>
        <author>Giada De Laurentiis</author>
        <year>2005</year>
        <price>30.00</price>
    </book>
    <book category="children">
        <title lang="en">Harry Potter</title>
        <author>J K. Rowling</author>
        <year>2005</year>
        <price>29.99</price>
    </book>
    <book category="web">
        <title lang="en">XQuery Kick Start</title>
        <author>James McGovern</author>
        <author>Per Bothner</author>
        <author>Kurt Cagle</author>
        <author>James Linn</author>
        <author>Vaidyanathan Nagarajan</author>
        <year>2003</year>
        <price>49.99</price>
    </book>
    <book category="web" cover="paperback">
        <title lang="en">Learning XML</title>
        <author>Erik T. Ray</author>
        <year>2003</year>
        <price>39.95</price>
    </book>
</bookstore>
```

在上面的 XML 中，根节点是 <bookstore>。文档中的所有其他节点都被包含在 <bookstore> 中。

根节点 <bookstore> 有四个 <book> 节点。

第一个 <book> 节点有四个节点：<title>、<author>、<year> 和 <price>，其中每个节点都包含一个文本节点，"Everyday Italian"、"Giada De Laurentiis"、"2005" 和 "30.00"。


## 文本总是存储在文本节点中

在 DOM 处理中一个普遍的错误是，认为元素节点包含文本。

不过，元素节点的文本是存储在文本节点中的。

在这个实例中：<year>2005</year>，元素节点 <year>，拥有一个值为 "2005" 的文本节点。

"2005" 不是 <year> 元素的值！


## 复习重点

- 能说明 `DOM 节点` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
