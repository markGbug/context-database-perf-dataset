# XSLT：XSLT <xsl:apply-templates> 元素

- 来源：[XSLT Apply](https://www.runoob.com/xsl/xsl-apple-templates.html)
- 分类：XML / Web Service
- 技术：XSLT
- 笔记类型：学习笔记
- 章节序号：4518

## 本章内容

<xsl:apply-templates> 元素可把一个模板应用于当前的元素或者当前元素的子节点。


## <xsl:apply-templates> 元素

<xsl:apply-templates> 元素可把一个模板应用于当前的元素或者当前元素的子节点。

假如我们向 <xsl:apply-templates> 元素添加一个 select 属性，此元素就会仅仅处理与属性值匹配的子元素。我们可以使用 select 属性来规定子节点被处理的顺序。

请看下面的 XSL 样式表：


## 实例

```html
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

<xsl:template match="/">
  <html>
  <body>
  <h2>My CD Collection</h2>
  <xsl:apply-templates/>
  </body>
  </html>
</xsl:template>

<xsl:template match="cd">
  <p>
  <xsl:apply-templates select="title"/>
  <xsl:apply-templates select="artist"/>
  </p>
</xsl:template>

<xsl:template match="title">
  Title: <span style="color:#ff0000">
  <xsl:value-of select="."/></span>
  <br />
</xsl:template>

<xsl:template match="artist">
  Artist: <span style="color:#00ff00">
  <xsl:value-of select="."/></span>
  <br />
</xsl:template>

</xsl:stylesheet>
```


## 复习重点

- 能说明 `XSLT Apply` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
