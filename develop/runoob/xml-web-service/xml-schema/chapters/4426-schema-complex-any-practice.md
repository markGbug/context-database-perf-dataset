# XML Schema：XSD <any> 元素

- 来源：[XML Schema any 元素](https://www.runoob.com/schema/schema-complex-any.html)
- 分类：XML / Web Service
- 技术：XML Schema
- 笔记类型：练习笔记
- 章节序号：4426

## 本章内容

<any> 元素使我们有能力通过未被 schema 规定的元素来拓展 XML 文档！


## <any> 元素

<any> 元素使我们有能力通过未被 schema 规定的元素来拓展 XML 文档！

下面这个例子是从名为 "family.xsd" 的 XML schema 中引用的片段。它展示了一个针对 "person" 元素的声明。通过使用 <any> 元素，我们可以通过任何元素（在 <lastname> 之后）扩展 "person" 的内容：

现在，我们希望使用 "children" 元素来扩展 "person" 元素。这此种情况下我们就可以这么做，即使以上这个 schema 的作者没有声明任何 "children" 元素。

请看这个 schema 文件，名为 "children.xsd"：

下面这个 XML 文件（名为 "Myfamily.xml"），使用了来自两个不同的 schema 中的成分，"family.xsd" 和 "children.xsd"：

上面这个 XML 文件是有效的，这是由于 schema "family.xsd" 允许我们通过在 "lastname" 元素后的可选元素来扩展 "person" 元素。

<any> 和 <anyAttribute> 均可用于制作可扩展的文档！它们使文档有能力包含未在主 XML schema 中声明过的附加元素。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XML Schema any 元素` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
