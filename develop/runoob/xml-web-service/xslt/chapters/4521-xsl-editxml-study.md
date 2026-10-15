# XSLT：XSLT - 编辑 XML

- 来源：[XSLT 编辑 XML](https://www.runoob.com/xsl/xsl-editxml.html)
- 分类：XML / Web Service
- 技术：XSLT
- 笔记类型：学习笔记
- 章节序号：4521

## 本章内容

存储在 XML 文件中的数据可通过因特网浏览器进行编辑。


## 打开、编辑并保存 XML

现在，我们会为您展示如何打开、编辑及保存存储于服务器上的 XML 文件。

我们将使用 XSL 把 XML 文档转换到一个 HTML 表单中。XML 元素的值会被写到 HTML 表单中的 HTML 输入域。这个 HTML 表单是可编辑的。在被编辑完成后，数据会被提交回服务器，XML 文件会得到更新（这部分由 ASP 完成）。


## XML 文件和 XSL 文件

首先，请看将被使用的 XML 文档（"tool.xml"）：

查看 XML 文件。

接着，请看下面的样式表（"tool.xsl"）：

查看 XSL 文件。

上面这个 XSL 文件会循环遍历 XML 文件中的元素，并为每个 XML "field" 元素创建一个输入域。XML "field" 元素的 "id" 属性的值被添加到每个 HTML 输入域的 "id" 和 "name" 属性。每个 XML "value" 元素的值被添加到每个 HTML 输入域的 "value" 属性。结果是，可以得到一个包含 XML 文件中值的可编辑的 HTML 表单。

然后，我们还有第二个样式表："tool_updated.xsl"。这个 XSL 文件会被用来显示已更新的 XML 数据。这个样式表不会输出可编辑 HTML 表单，而是一个静态的 HTML 表格：

查看 XSL 文件。


## ASP 文件

在上面 "tool.xsl" 文件中，HTML 表单的 action 属性的值是 "edittool.asp" 。

"edittool.asp" 页面包含两个函数：loadFile() 函数载入并转换 XML 文件，updateFile() 函数更新 XML 文件：

提示：假如您不了解如何编写 ASP，请学习我们的 ASP 教程。

注意：我们正在转换并更新位于服务器上的 XML 文件。这是一个跨平台的解决方案。客户端仅能获得从服务器返回的 HTML - 而 HTML 可运行于任何浏览器。


## 复习重点

- 能说明 `XSLT 编辑 XML` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
