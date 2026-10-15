# XML：XML Parser

- 来源：[XML 解析器](https://www.runoob.com/xml/xml-parser.html)
- 分类：XML / Web Service
- 技术：XML
- 笔记类型：练习笔记
- 章节序号：4450

## 本章内容

所有现代浏览器都有内建的 XML 解析器。

XML 解析器把 XML 文档转换为 XML DOM 对象 - 可通过 JavaScript 操作的对象。


## 解析 XML 文档

下面的代码片段把 XML 文档解析到 XML DOM 对象中：


## 解析 XML 字符串

下面的代码片段把 XML 字符串解析到 XML DOM 对象中：

注释：Internet Explorer 使用 loadXML() 方法来解析 XML 字符串，而其他浏览器使用 DOMParser 对象。


## 跨域访问

出于安全方面的原因，现代的浏览器不允许跨域的访问。

这意味着，网页以及它试图加载的 XML 文件，都必须位于相同的服务器上。


## XML DOM

在下一章中，您将学习如何访问 XML DOM 对象并取回数据。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XML 解析器` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
