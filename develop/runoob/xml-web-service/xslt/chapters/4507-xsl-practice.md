# XSLT：XSLT 教程

- 来源：[XSLT 教程](https://www.runoob.com/xsl/xsl-tutorial.html)
- 分类：XML / Web Service
- 技术：XSLT
- 笔记类型：练习笔记
- 章节序号：4507

## 本章内容

XSL 指扩展样式表语言（EXtensible Stylesheet Language）, 它是一个 XML 文档的样式表语言。

XSLT 指 XSL 转换。在此教程中，你将学习如何使用 XSLT 将 XML 文档转换为其他文档，比如 XHTML。

现在开始学习 XSLT !

在线 XSLT 转换工具 – XML 转 HTML 在线预览


## XSLT 实例

```html
<?xml version="1.0"?>

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
          <td><xsl:value-of select="artist"/></td>
        </tr>
      </xsl:for-each>
    </table>
  </body>
  </html>
</xsl:template>

</xsl:stylesheet>
```


## XSLT 参考手册

XSLT 元素 对所有来自 W3C 标准的 XSLT 元素进行了描述，以及关于浏览器支持的信息。

XSLT 函数 XSLT 包含了超过 100 个内置函数。 这些函数可以用于字符串、数值、日期和时间比较、节点和 QName 处理, 序列处理, 逻辑值等等。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XSLT 教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
