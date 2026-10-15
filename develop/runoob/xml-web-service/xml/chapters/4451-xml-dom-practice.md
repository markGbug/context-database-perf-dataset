# XML：XML DOM

- 来源：[XML DOM](https://www.runoob.com/xml/xml-dom.html)
- 分类：XML / Web Service
- 技术：XML
- 笔记类型：练习笔记
- 章节序号：4451

## 本章内容

DOM（Document Object Model 文档对象模型）定义了访问和操作文档的标准方法。


## XML DOM

XML DOM（XML Document Object Model）定义了访问和操作 XML 文档的标准方法。

XML DOM 把 XML 文档作为树结构来查看。

所有元素可以通过 DOM 树来访问。可以修改或删除它们的内容，并创建新的元素。元素，它们的文本，以及它们的属性，都被认为是节点。

在我们的 XML DOM 教程中，您可以学习更多有关 XML DOM 的知识。


## HTML DOM

HTML DOM 定义了访问和操作 HTML 文档的标准方法。

所有 HTML 元素可以通过 HTML DOM 来访问。

在我们的 HTML DOM 教程中，您可以学习更多有关 HTML DOM 的知识。.


## 加载一个 XML 文件 - 跨浏览器实例

下面的实例把 XML 文档（"note.xml"）解析到 XML DOM 对象中，然后通过 JavaScript 提取一些信息：


## 实例


## 重要注释！

如需从上面的 XML 文件（"note.xml"）的 <to> 元素中提取文本 "Tove"，语法是：

请注意，即使 XML 文件只包含一个 <to> 元素，您仍然必须指定数组索引 [0]。这是因为 getElementsByTagName() 方法返回一个数组。


## 加载一个 XML 字符串 - 跨浏览器实例

下面的实例把 XML 字符串解析到 XML DOM 对象中，然后通过 JavaScript 提取一些信息：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XML DOM` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
