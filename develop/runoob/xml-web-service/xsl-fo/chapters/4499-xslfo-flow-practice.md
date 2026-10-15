# XSL-FO：XSL-FO 流

- 来源：[XSLFO 流](https://www.runoob.com/xslfo/xslfo-flow.html)
- 分类：XML / Web Service
- 技术：XSL-FO
- 笔记类型：练习笔记
- 章节序号：4499

## 本章内容

XSL-FO 页面使用来自 <fo:flow> 元素的数据进行填充。


## XSL-FO 页面序列（Page Sequences）

XSL-FO 使用 <fo:page-sequence> 元素来定义输出页面。

每个输出页面都会引用一个定义布局的 page master。

每个输出页面都有一个定义输出的 <fo:flow> 元素。

每个输出页面均会按序列（顺序）被打印或显示。


## XSL-FO 流（Flow）

XSL-FO 页面使用来自 <fo:flow> 元素的内容进行填充。

<fo:flow> 元素包含所有被打印到页面的元素。

当页面被印满以后，相同的 page master 会被一遍又一遍地被使用，直到所有文本被打印为止。


## 流动到何处？

<fo:flow> 元素有一个 "flow-name" 属性。

flow-name 属性的值定义 <fo:flow> 元素的内容会去往何处。

合法的值：

- xsl-region-body（进入 region-body）
- xsl-region-before（进入 region-before）
- xsl-region-after（进入 region-after）
- xsl-region-start（进入 region-start）
- xsl-region-end（进入 region-end）


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XSLFO 流` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
