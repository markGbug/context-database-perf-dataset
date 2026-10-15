# XSLT：XSLT - 转换

- 来源：[XSLT 转换](https://www.runoob.com/xsl/xsl-transformation.html)
- 分类：XML / Web Service
- 技术：XSLT
- 笔记类型：练习笔记
- 章节序号：4511

## 本章内容

实例研究：如何使用 XSLT 将 XML 转换为 XHTML。

我们会在下一章对本实例的细节进行解释。


## 正确的样式表声明

把文档声明为 XSL 样式表的根元素是 <xsl:stylesheet> 或 <xsl:transform>。

注意：<xsl:stylesheet> 和 <xsl:transform> 是完全同义的，均可被使用！

根据 W3C 的 XSLT 标准，声明 XSL 样式表的正确方法是：

或者：

如需访问 XSLT 的元素、属性以及特性，我们必须在文档顶端声明 XSLT 命名空间。

xmlns:xsl="http://www.w3.org/1999/XSL/Transform" 指向了官方的 W3C XSLT 命名空间。如果您使用此命名空间，就必须包含属性 version="1.0"。


## 从一个原始的 XML 文档开始

我们现在要把下面这个 XML 文档（"cdcatalog.xml"）转换为 XHTML：

在 Firefox 和 Internet Explorer 中查看 XML 文件：打开 XML 文件（通常通过点击某个链接） - XML 文档会以颜色化的代码方式来显示根元素及子元素。点击元素左侧的加号（+）或减号（-）可展开或收缩元素的结构。如需查看原始的 XML 源文件（不带有加号和减号），请在浏览器菜单中选择"查看页面源代码"或"查看源代码"。

在 Netscape 6 中查看 XML 文件：打开 XML 文件，然后在 XML 文件中右击，并选择"查看页面源代码"。XML 文档会以颜色化的代码方式来显示根元素及子元素。

在 Opera 7 中查看 XML 文件：打开 XML 文件，然后在 XML 文件中右击，选择"框架"/"查看源代码"。XML 文档将显示为纯文本。

查看 "cdcatalog.xml"


## 创建 XSL 样式表

然后创建一个带有转换模板的 XSL 样式表（"cdcatalog.xsl"）：

查看 "cdcatalog.xsl"


## 把 XSL 样式表链接到 XML 文档

向 XML 文档（"cdcatalog.xml"）添加 XSL 样式表引用：

如果您使用的浏览器兼容 XSLT，它会很顺利地把您的 XML 转换为 XHTML。

查看结果

我们会在下一章对上面的例子中的细节进行解释。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XSLT 转换` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
