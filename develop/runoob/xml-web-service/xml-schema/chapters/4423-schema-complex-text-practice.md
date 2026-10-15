# XML Schema：XSD 仅含文本

- 来源：[XML Schema 复合元素 - 仅含文本](https://www.runoob.com/schema/schema-complex-text.html)
- 分类：XML / Web Service
- 技术：XML Schema
- 笔记类型：练习笔记
- 章节序号：4423

## 本章内容

仅含文本的复合元素可包含文本和属性。


## 仅含文本的复合元素

此类型仅包含简易的内容（文本和属性），因此我们要向此内容添加 simpleContent 元素。当使用简易内容时，我们就必须在 simpleContent 元素内定义扩展或限定，就像这样：

提示： 请使用 extension 或 restriction 元素来扩展或限制元素的基本简易类型。 这里有一个 XML 元素的例子，"shoesize"，其中仅包含文本：

下面这个例子声明了一个复合类型，其内容被定义为整数值，并且 "shoesize" 元素含有名为 "country" 的属性：

我们也可为 complexType 元素设定一个名称，并让 "shoesize" 元素的 type 属性来引用此名称（通过使用此方法，若干元素均可引用相同的复合类型）：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XML Schema 复合元素 - 仅含文本` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
