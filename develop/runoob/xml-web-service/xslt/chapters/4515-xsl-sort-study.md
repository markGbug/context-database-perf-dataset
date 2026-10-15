# XSLT：XSLT <xsl:sort> 元素

- 来源：[XSLT <sort>](https://www.runoob.com/xsl/xsl-sort.html)
- 分类：XML / Web Service
- 技术：XSLT
- 笔记类型：学习笔记
- 章节序号：4515

## 本章内容

<xsl:sort> 元素用于对输出结果进行排序。


## 在何处放置排序信息

如需对输出结果进行排序，只要简单地在 XSL 文件中的 <xsl:for-each> 元素内部添加一个 <xsl:sort> 元素：


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
    <xsl:for-each select="catalog/cd">
      <xsl:sort select="artist"/>
      <tr>
        <td><xsl:value-of select="title"/></td>
        <td><xsl:value-of select="artist"/></td>
      </tr>
    </xsl:for-each>
  </table>
  </body>
  </html>
</xsl:template>

</xsl:stylesheet>
```

注意：select 属性指示需要排序的 XML 元素。


## 复习重点

- 能说明 `XSLT <sort>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
