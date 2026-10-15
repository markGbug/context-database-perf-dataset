# XML DOM：XML DOM 创建节点

- 来源：[DOM 创建节点](https://www.runoob.com/dom/dom-nodes-create.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：练习笔记
- 章节序号：4389

## 本章内容

## 尝试一下 - 实例

下面的实例使用 XML 文件 books.xml。 函数 loadXMLDoc()，位于外部 JavaScript 中，用于加载 XML 文件。

创建元素节点 本例使用 createElement() 来创建一个新的元素节点，并使用 appendChild() 把它添加到一个节点中。

使用 createAttribute 创建属性节点 本例使用 createAttribute() 来创建一个新的属性节点，并使用 setAttributeNode() 把它插入一个元素中。

使用 setAttribute 创建属性节点 本例使用 setAttribute() 为一个元素创建一个新的属性。

创建文本节点 本例使用 createTextNode() 来创建一个新的文本节点，并使用 appendChild() 把它添加到一个元素中。

创建 CDATA section 节点 本例使用 createCDATAsection() 来创建一个 CDATA section 节点，并使用 appendChild() 把它添加到一个元素中。

创建注释节点 本例使用 createComment() 来创建一个注释节点，并使用 appendChild() 把它添加到一个元素中。


## 创建新的元素节点

createElement() 方法创建一个新的元素节点：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 创建一个新的元素节点 <edition>
- 向第一个 <book> 元素追加这个元素节点

遍历并向所有 <book> 元素添加一个元素： 尝试一下


## 创建新的属性节点

createAttribute() 用于创建一个新的属性节点：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 创建一个新的属性节点 "edition"
- 设置属性节点的值为 "first"
- 向第一个 <title> 元素添加这个新的属性节点

遍历所有的 <title> 元素，并添加一个新的属性节点： 尝试一下

注意：如果该属性已存在，则被新属性替代。


## 使用 setAttribute() 创建属性

由于 setAttribute() 方法可以在属性不存在的情况下创建新的属性，我们可以使用这个方法来创建一个新的属性。


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 为第一个 <book> 元素设置（创建）值为 "first" 的 "edition" 属性

遍历所有的 <title> 元素并添加一个新属性： 尝试一下


## 创建文本节点

createTextNode() 方法创建一个新的文本节点：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 创建一个新元素节点 <edition>
- 创建一个新的文本节点，其文本是 "first"
- 向这个元素节点追加新的文本节点
- 向第一个 <book> 元素追加新的元素节点

向所有的 <book> 元素添加一个带有文本节点的元素节点： 尝试一下


## 创建 CDATA Section 节点

createCDATASection() 方法创建一个新的 CDATA section 节点。


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 创建一个新的 CDATA section 节点
- 向第一个 <book> 元素追加这个新的 CDATA section 节点

遍历并向所有 <book> 元素添加一个 CDATA section： 尝试一下


## 创建注释节点

createComment() 方法创建一个新的注释节点。


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 创建一个新的注释节点
- 把这个新的注释节点追加到第一个 <book> 元素

循环并向所有 <book> 元素添加一个注释节点： 尝试一下


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM 创建节点` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
