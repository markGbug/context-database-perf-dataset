# XSL-FO：XSL-FO 文档

- 来源：[XSLFO 文档](https://www.runoob.com/xslfo/xslfo-documents.html)
- 分类：XML / Web Service
- 技术：XSL-FO
- 笔记类型：学习笔记
- 章节序号：4496

## 本章内容

## XSL-FO 文档

XSL-FO 文档是带有输出信息的 XML 文件。

XSL-FO 文档存储在以 .fo 或 .fob 为文件扩展名的文件中。您也可以把 XSL-FO 文档存储为以 .xml 为扩展名的文件，这样做的话可以使 XSL-FO 文档更易被 XML 编辑器存取。


## XSL-FO 文档结构

XSL-FO 的文档结构如下所示：


## 结构解释

XSL-FO 文档属于 XML 文档，因此也需要以 XML 声明来起始：

<fo:root> 元素是 XSL-FO 文档的根元素。这个根元素也要声明 XSL-FO 的命名空间：

<fo:layout-master-set> 元素包含一个或多个页面模板：

每个 <fo:simple-page-master> 元素包含一个单一的页面模板。每个模板必须有一个唯一的名称（master-name）：

一个或多个 <fo:page-sequence> 元素可描述页面内容。master-reference 属性使用相同的名称来引用 simple-page-master 模板：

注释：master-reference 的值 "A4" 实际上并没有描述某个预定义的页面格式。它仅仅是一个名称。您可以使用任何名称，比如 "MyPage"、"MyTemplate" 等等。


## 复习重点

- 能说明 `XSLFO 文档` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
