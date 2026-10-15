# XPath：XPath Examples

- 来源：[XPath 实例](https://www.runoob.com/xpath/xpath-examples.html)
- 分类：XML / Web Service
- 技术：XPath
- 笔记类型：学习笔记
- 章节序号：4472

## 本章内容

在本节，让我们通过实例来学习一些基础的 XPath 语法。


## XML实例文档

我们将在下面的例子中使用这个 XML 文档：

"books.xml":

在您的浏览器中查看此 "books.xml" 文件。


## 加载 XML 文档

所有现代浏览器都支持使用 XMLHttpRequest 来加载 XML 文档的方法。

针对大多数现代浏览器的代码：

针对古老的微软浏览器（IE 5 和 6）的代码：


## 选取节点

不幸的是，Internet Explorer 和其他处理 XPath 的方式不同。

在我们的例子中，包含适用于大多数主流浏览器的代码。

Internet Explorer 使用 selectNodes() 方法从 XML 文档中的选取节点：

Firefox、Chrome、Opera 以及 Safari 使用 evaluate() 方法从 XML 文档中选取节点：


## 选取所有 title

下面的例子选取所有 title 节点：


## 实例


## 选取第一个 book 的 title

下面的例子选取 bookstore 元素下面的第一个 book 节点的 title：


## 实例

这里有一个问题。上面的例子在 IE 和其他浏览器中输出不同的结果。

IE5 以及更高版本将 [0] 视为第一个节点，而根据 W3C 的标准，应该是 [1]。


### 一种解决方法！

为了解决 IE5+ 中 [0] 和 [1] 的问题，可以为 XPath 设置语言选择（SelectionLanguage）。

下面的例子选取 bookstore 元素下面的第一个 book 节点的 title：


## 实例


## 选取所有价格

下面的例子选取 price 节点中的所有文本：


## 实例


## 选取价格高于 35 的 price 节点

下面的例子选取价格高于 35 的所有 price 节点：


## 实例


## 选取价格高于 35 的 title 节点

下面的例子选取价格高于 35 的所有 title 节点：


## 实例


## 复习重点

- 能说明 `XPath 实例` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
