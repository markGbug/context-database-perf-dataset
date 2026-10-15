# XSLT：XSLT <xsl:choose> 元素

- 来源：[XSLT <choose>](https://www.runoob.com/xsl/xsl-choose.html)
- 分类：XML / Web Service
- 技术：XSLT
- 笔记类型：练习笔记
- 章节序号：4517

## 本章内容

<xsl:choose> 元素用于结合 <xsl:when> 和 <xsl:otherwise> 来表达多重条件测试。


## <xsl:choose> 元素


### 语法


## 在何处放置选择条件

如需插入针对 XML 文件的多重条件测试，请向 XSL 文件添加 <xsl:choose>、<xsl:when> 以及 <xsl:otherwise> 元素：


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
    <tr>
      <td><xsl:value-of select="title"/></td>
      <xsl:choose>
        <xsl:when test="price > 10">
          <td bgcolor="#ff00ff">
          <xsl:value-of select="artist"/></td>
        </xsl:when>
        <xsl:otherwise>
          <td><xsl:value-of select="artist"/></td>
        </xsl:otherwise>
      </xsl:choose>
    </tr>
    </xsl:for-each>
  </table>
  </body>
  </html>
</xsl:template>

</xsl:stylesheet>
```

上面的代码会在 CD 的价格高于 10 时向 "Artist" 列添加粉色的背景颜色。


## 另一个实例

这是另外一个包含两个 <xsl:when> 元素的实例：


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
    <tr>
      <td><xsl:value-of select="title"/></td>
      <xsl:choose>
        <xsl:when test="price > 10">
          <td bgcolor="#ff00ff">
          <xsl:value-of select="artist"/></td>
        </xsl:when>
        <xsl:when test="price > 9">
          <td bgcolor="#cccccc">
          <xsl:value-of select="artist"/></td>
        </xsl:when>
        <xsl:otherwise>
          <td><xsl:value-of select="artist"/></td>
        </xsl:otherwise>
      </xsl:choose>
    </tr>
    </xsl:for-each>
  </table>
  </body>
  </html>
</xsl:template>

</xsl:stylesheet>
```

上面的代码会在 CD 的价格高于 10 时向 "Artist" 列添加粉色的背景颜色，并在 CD 的价格高于 9 且低于等于 10 时向 "Artist" 列添加灰色的背景颜色。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XSLT <choose>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
