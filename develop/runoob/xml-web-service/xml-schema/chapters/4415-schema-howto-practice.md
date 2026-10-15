# XML Schema：XSD 如何使用?

- 来源：[如何使用 XML Schema](https://www.runoob.com/schema/schema-howto.html)
- 分类：XML / Web Service
- 技术：XML Schema
- 笔记类型：练习笔记
- 章节序号：4415

## 本章内容

XML 文档可对 DTD 或 XML Schema 进行引用。


## 一个简单的 XML 文档：

请看这个名为 "note.xml" 的 XML 文档：


## DTD 文件

下面这个例子是名为 "note.dtd" 的 DTD 文件，它对上面那个 XML 文档（ "note.xml" ）的元素进行了定义：

第 1 行定义 note 元素有四个子元素："to, from, heading, body"。

第 2-5 行定义了 to, from, heading, body 元素的类型是 "#PCDATA"。


## XML Schema

下面这个例子是一个名为 "note.xsd" 的 XML Schema 文件，它定义了上面那个 XML 文档（ "note.xml" ）的元素：

note 元素是一个复合类型，因为它包含其他的子元素。其他元素 (to, from, heading, body) 是简易类型，因为它们没有包含其他元素。您将在下面的章节学习更多有关复合类型和简易类型的知识。


## 对 DTD 的引用

此文件包含对 DTD 的引用：


## 对 XML Schema 的引用

此文件包含对 XML Schema 的引用：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `如何使用 XML Schema` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
