# XSL-FO：XSL-FO 输出

- 来源：[XSLFO 输出](https://www.runoob.com/xslfo/xslfo-output.html)
- 分类：XML / Web Service
- 技术：XSL-FO
- 笔记类型：练习笔记
- 章节序号：4498

## 本章内容

XSL-FO 在 <fo:flow> 元素内部定义输出。


## XSL-FO 页面（Page）、流（Flow）以及块（Block）

内容"块"会"流"入"页面"中，然后输出到媒介。

XSL-FO 输出通常被嵌套在 <fo:block> 元素内，<fo:block> 嵌套于 <fo:flow> 元素内，<fo:flow> 嵌套于 <fo:page-sequence> 元素内：


## XSL-FO 实例

现在让我们看一个真实的 XSL-FO 实例：

以上代码的输出如下所示：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XSLFO 输出` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
