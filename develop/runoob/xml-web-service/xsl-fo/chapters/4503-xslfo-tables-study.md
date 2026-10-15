# XSL-FO：XSL-FO 表格

- 来源：[XSLFO 表格](https://www.runoob.com/xslfo/xslfo-tables.html)
- 分类：XML / Web Service
- 技术：XSL-FO
- 笔记类型：学习笔记
- 章节序号：4503

## 本章内容

XSL-FO 使用 <fo:table-and-caption> 元素来定义表格。


## XSL-FO 表格（Tables）

XSL-FO 表格模型与 HTML 表格模型不是完全不同的。

有九种 XSL-FO 对象可用来创建表格：

- fo:table-and-caption
- fo:table
- fo:table-caption
- fo:table-column
- fo:table-header
- fo:table-footer
- fo:table-body
- fo:table-row
- fo:table-cell

XSL-FO 使用 <fo:table-and-caption> 元素来定义表格。它包含一个 <fo:table> 以及一个可选的 <fo:caption> 元素。

<fo:table> 元素包含可选的 <fo:table-column> 元素，一个可选的 <fo:table-header> 元素，一个 <fo:table-body> 元素，一个可选的 <fo:table-footer> 元素。这些元素中的每一个都可能拥有一个或多个 <fo:table-row> 元素，而 <fo:table-row> 同时会带有一个或多个 <fo:table-cell> 元素：

以上代码的输出如下所示：


## 复习重点

- 能说明 `XSLFO 表格` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
