# XSLT：XSLT <xsl:template> 元素

- 来源：[XSLT <template>](https://www.runoob.com/xsl/xsl-templates.html)
- 分类：XML / Web Service
- 技术：XSLT
- 笔记类型：学习笔记
- 章节序号：4512

## 本章内容

XSL 样式表由一个或多套被称为模板（template）的规则组成。

每个模板含有当某个指定的节点被匹配时所应用的规则。


## <xsl:template> 元素

<xsl:template> 元素用于构建模板。

match 属性用于关联 XML 元素和模板。match 属性也可用来为整个 XML 文档定义模板。match 属性的值是 XPath 表达式（举例，match="/" 定义整个文档）。

好了，让我们看一下上一章中的 XSL 文件的简化版本：


## 实例

```html
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

<xsl:template match="/">
  <html>
  <body>
  <h2>My CD Collection</h2>
  <table border="1">
    <tr bgcolor="#9acd32">
      <th>Title</th>
      <th>Artist</th>
    </tr>
    <tr>
      <td>.</td>
      <td>.</td>
    </tr>
  </table>
  </body>
  </html>
</xsl:template>

</xsl:stylesheet>
```


## 实例解释

由于 XSL 样式表本身也是一个 XML 文档，因此它总是由 XML 声明起始：<?xml version="1.0" encoding="ISO-8859-1"?>.

下一个元素，<xsl:stylesheet>， ，定义此文档是一个 XSLT 样式表文档（连同版本号和 XSLT 命名空间属性）。

<xsl:template> 元素定义了一个模板。而 match="/" 属性则把此模板与 XML 源文档的根相联系。

<xsl:template> 元素内部的内容定义了写到输出结果的 HTML 代码。

最后两行定义了模板的结尾及样式表的结尾。

这个实例的结果有一点小缺陷，因为数据没有从 XML 文档被复制到输出。在下一章中，您将学习到如何使用 <xsl:value-of> 元素从 XML 元素选取值。


## 复习重点

- 能说明 `XSLT <template>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
