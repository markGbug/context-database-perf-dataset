# XML Schema：XSD 混合内容

- 来源：[XML Schema 复合类型 - 混合内容](https://www.runoob.com/schema/schema-complex-mixed.html)
- 分类：XML / Web Service
- 技术：XML Schema
- 笔记类型：学习笔记
- 章节序号：4424

## 本章内容

混合的复合类型可包含属性、元素以及文本。


## 带有混合内容的复合类型

XML 元素，"letter"，含有文本以及其他元素：

下面这个 schema 声明了这个 "letter" 元素：

注意： 为了使字符数据可以出现在 "letter" 的子元素之间，mixed 属性必须被设置为 "true"。<xs:sequence> 标签 (name、orderid 以及 shipdate ) 意味着被定义的元素必须依次出现在 "letter" 元素内部。

我们也可以为 complexType 元素起一个名字，并让 "letter" 元素的 type 属性引用 complexType 的这个名称（通过这个方法，若干元素均可引用同一个复合类型）：


## 复习重点

- 能说明 `XML Schema 复合类型 - 混合内容` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
