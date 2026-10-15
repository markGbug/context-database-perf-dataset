# XSLT：XSLT - 在服务器端

- 来源：[XSLT 服务器端](https://www.runoob.com/xsl/xsl-server.html)
- 分类：XML / Web Service
- 技术：XSLT
- 笔记类型：练习笔记
- 章节序号：4520

## 本章内容

由于并非所有的浏览器都支持 XSLT，另一种解决方案是在服务器上完成 XML 至 XHTML 的转化。


## 跨浏览器解决方案

为了让 XML 数据适用于任何类型的浏览器，我们必须在服务器上对 XML 文档进行转换，然后将其作为 XHMTL 发送回浏览器。

这是 XSLT 的另一个优点。XSLT 的设计目标之一是使数据在服务器上从一种格式转换到另一种格式成为可能，并向所有类型的浏览器返回可读的数据。


## XML 文件和 XSLT 文件

请看这个在前面的章节已展示过的 XML 文档：

```html
<?xml version="1.0" encoding="UTF-8"?>
<catalog>
  <cd>
    <title>Empire Burlesque</title>
    <artist>Bob Dylan</artist>
    <country>USA</country>
    <company>Columbia</company>
    <price>10.90</price>
    <year>1985</year>
  </cd>
.
.
</catalog>
```

查看 XML 文件。

以及附随的 XSL 样式表：

```html
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

<xsl:template match="/">
  <h2>My CD Collection</h2>
  <table border="1">
    <tr bgcolor="#9acd32">
      <th style="text-align:left">Title</th>
      <th style="text-align:left">Artist</th>
    </tr>
    <xsl:for-each select="catalog/cd">
    <tr>
      <td><xsl:value-of select="title" /></td>
      <td><xsl:value-of select="artist" /></td>
    </tr>
    </xsl:for-each>
  </table>
</xsl:template>

</xsl:stylesheet>
```

查看 XSL 文件。

请注意，这个 XML 文件没有包含对 XSL 文件的引用。

重要事项：上面这句话意味着，XML 文件可使用多个不同的 XSL 样式表来进行转换。


## 在服务器把 XML 转换为 XHTML

这是用于在服务器上把 XML 文件转换为 XHTML 的源代码：


### 使用 PHP 代码转换：

```text
<?php
// 载入 XML 文件
$xml = new DOMDocument;
$xml->load('cdcatalog.xml');

// 载入 XSL 文件
$xsl = new DOMDocument;
$xsl->load('cdcatalog.xsl');

// 设置转换
$proc = new XSLTProcessor;

// 添加 xsl 规则
$proc->importStyleSheet($xsl);

echo $proc->transformToXML($xml);
?>
```

提示：假如您不了解如何编写 php，您可以学习我们的 PHP 教程。


### 使用 ASP 代码转换：

```text
<%
'载入 XML 文件
set xml = Server.CreateObject("Microsoft.XMLDOM")
xml.async = false
xml.load(Server.MapPath("cdcatalog.xml"))

'载入 XSL 文件
set xsl = Server.CreateObject("Microsoft.XMLDOM")
xsl.async = false
xsl.load(Server.MapPath("cdcatalog.xsl"))

'转换文件
Response.Write(xml.transformNode(xsl))
%>
```

提示：假如您不了解如何编写 ASP，您可以学习我们的 ASP 教程。

第一段代码创建了微软的 XML 解析器（XMLDOM）的一个实例，并把 XML 文件载入了内存。第二段代码创建了解析器的另一个实例，并把这个 XSL 文件载入了内存。最后一行代码使用 XSL 文档转换了 XML 文档，并把结果作为 XHTML 发送到您的浏览器。太好了！

它是如何工作的。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XSLT 服务器端` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
