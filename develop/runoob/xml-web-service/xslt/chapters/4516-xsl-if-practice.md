# XSLT：XSLT <xsl:if> 元素

- 来源：[XSLT <if>](https://www.runoob.com/xsl/xsl-if.html)
- 分类：XML / Web Service
- 技术：XSLT
- 笔记类型：练习笔记
- 章节序号：4516

## 本章内容

<xsl:if> 元素用于对 XML 数据执行条件判断，当指定条件成立时才输出对应内容。


## <xsl:if> 元素

在 XSLT 中，如果需要根据 XML 节点的值或状态来决定是否输出某段内容，可以使用 <xsl:if> 元素进行条件控制。


### 语法

说明：test 属性用于指定条件表达式（XPath 表达式），当表达式结果为 true 时，内部内容才会被处理和输出。


## 在何处放置 <xsl:if> 元素

通常情况下，<xsl:if> 会配合循环语句一起使用，例如在 <xsl:for-each> 中对每个节点进行筛选：


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
      <th>Price</th>
    </tr>
    <xsl:for-each select="catalog/cd">
      <xsl:if test="price > 10">
        <tr>
          <td><xsl:value-of select="title"/></td>
          <td><xsl:value-of select="artist"/></td>
          <td><xsl:value-of select="price"/></td>
        </tr>
      </xsl:if>
    </xsl:for-each>
  </table>
  </body>
  </html>
</xsl:template>

</xsl:stylesheet>
```

注意：test 属性是必需的，其值为 XPath 表达式，例如比较运算（>、<、=）或逻辑判断。

说明：上述示例中，仅当 price 大于 10 时，对应的 CD 才会被输出到表格中。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XSLT <if>` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
