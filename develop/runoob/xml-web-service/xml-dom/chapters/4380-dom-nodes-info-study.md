# XML DOM：XML DOM 节点信息

- 来源：[DOM 节点信息](https://www.runoob.com/dom/dom-nodes-info.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4380

## 本章内容

nodeName、nodeValue 和 nodeType 属性包含有关节点的信息。


## 尝试一下 - 实例

下面的实例使用 XML 文件 books.xml。 函数 loadXMLDoc()，位于外部 JavaScript 中，用于加载 XML 文件。

获取元素节点的节点名称 本例使用 nodeName 属性来获取 "books.xml" 中根元素的节点名称。

从文本节点获取文本 本例使用 nodeValue 属性来获取 "books.xml" 中第一个 <title> 元素的文本。

更改文本节点中的文本 本例使用 nodeValue 属性来更改 "books.xml" 中第一个 <title> 元素的文本。

获取元素节点的节点名称和类型 本例使用 nodeName 和 nodeType 属性来获取 "books.xml" 中根元素的节点名称和类型。


## 节点的属性

在 XML DOM 中，每个节点都是一个对象。

对象拥有方法和属性，并可通过 JavaScript 进行访问和操作。

三个重要的节点属性是：

- nodeName
- nodeValue
- nodeType


## nodeName 属性

nodeName 属性规定节点的名称。

- nodeName 是只读的
- 元素节点的 nodeName 与标签名相同
- 属性节点的 nodeName 是属性的名称
- 文本节点的 nodeName 永远是 #text
- 文档节点的 nodeName 永远是 #document

尝试一下.


## nodeValue 属性

nodeValue 属性规定节点的值。

- 元素节点的 nodeValue 是 undefined
- 文本节点的 nodeValue 是文本本身
- 属性节点的 nodeValue 是属性的值


## 获取元素的值

下面的代码检索第一个 <title> 元素的文本节点的值：


## 实例

```text
xmlDoc=loadXMLDoc("books.xml");

x=xmlDoc.getElementsByTagName("title")[0].childNodes[0];
txt=x.nodeValue;
```

结果：txt = "Everyday Italian"

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取第一个 <title> 元素节点的文本节点
- 把 txt 变量设置为文本节点的值


## 更改元素的值

下面的代码更改第一个 <title> 元素的文本节点的值：


## 实例

```text
xmlDoc=loadXMLDoc("books.xml");

x=xmlDoc.getElementsByTagName("title")[0].childNodes[0];
x.nodeValue="Easy Cooking";
```

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取第一个 <title> 元素节点的文本节点
- 更改文本节点的值为 "Easy Cooking"


## nodeType 属性

nodeType 属性规定节点的类型。

nodeType 是只读的。

最重要的节点类型是：

尝试一下。


## 复习重点

- 能说明 `DOM 节点信息` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
