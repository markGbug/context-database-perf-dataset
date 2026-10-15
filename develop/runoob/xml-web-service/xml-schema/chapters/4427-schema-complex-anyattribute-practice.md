# XML Schema：XSD <anyAttribute> 元素

- 来源：[XML Schema anyAttribute 元素](https://www.runoob.com/schema/schema-complex-anyattribute.html)
- 分类：XML / Web Service
- 技术：XML Schema
- 笔记类型：练习笔记
- 章节序号：4427

## 本章内容

<anyAttribute> 元素使我们有能力通过未被 schema 规定的属性来扩展 XML 文档！

下面的例子是来自名为 "family.xsd" 的 XML schema 的一个片段。它为我们展示了针对 "person" 元素的一个声明。通过使用 <anyAttribute> 元素，我们就可以向 "person" 元素添加任意数量的属性：

现在，我们希望通过 "gender" 属性来扩展 "person" 元素。在这种情况下我们就可以这样做，即使这个 schema 的作者从未声明过任何 "gender" 属性。

请看这个 schema 文件，名为 "attribute.xsd"：

下面这个 XML（名为 "Myfamily.xml"），使用了来自不同 schema 的成分，"family.xsd" 和 "attribute.xsd"：

上面这个 XML 文件是有效的，这是因为 schema "family.xsd" 允许我们向 "person" 元素添加属性。

<any> 和 <anyAttribute> 均可用于制作可扩展的文档！它们使文档有能力包含未在主 XML schema 中声明过的附加元素。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XML Schema anyAttribute 元素` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
