# XML Schema：XSD 仅含元素

- 来源：[XML Schema 复合类型 - 仅含元素](https://www.runoob.com/schema/schema-complex-elements.html)
- 分类：XML / Web Service
- 技术：XML Schema
- 笔记类型：学习笔记
- 章节序号：4422

## 本章内容

"仅含元素"的复合类型元素是只能包含其他元素的元素。


## 复合类型仅包含元素

XML 元素，"person"，仅包含其他的元素：

您可在 schema 中这样定义 "person" 元素：

请留意这个 。它意味着被定义的元素必须按上面的次序出现在 "person" 元素中。

或者您可以为 complexType 元素设定一个名称，并让 "person" 元素的 type 属性来引用此名称（如使用此方法，若干元素均可引用相同的复合类型）：


## 复习重点

- 能说明 `XML Schema 复合类型 - 仅含元素` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
