# XSLT：XSLT <xsl:value-of> 元素

- 来源：[XSLT <value-of>](https://www.runoob.com/xsl/xsl-value-of.html)
- 分类：XML / Web Service
- 技术：XSLT
- 笔记类型：练习笔记
- 章节序号：4513

## 本章内容

<xsl:value-of> 元素用于提取某个选定节点的值。


## <xsl:value-of> 元素

<xsl:value-of> 元素用于提取某个 XML 元素的值，并把值添加到转换的输出流中：


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
      <td><xsl:value-of select="catalog/cd/title"/></td>
      <td><xsl:value-of select="catalog/cd/artist"/></td>
    </tr>
  </table>
  </body>
  </html>
</xsl:template>

</xsl:stylesheet>
```


## 实例解释

注意：在上面的实例中，select 属性的值是一个 XPath 表达式。这个 XPath 表达式的工作方式类似于定位某个文件系统，在其中正斜杠（/）可选择子目录。

上面实例的结果有一点小缺陷，仅有一行数据从 XML 文档被复制到输出。在下一章中，您将学习到如何使用 <xsl:for-each> 元素来循环遍历 XML 元素，并显示所有的记录。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XSLT <value-of>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
