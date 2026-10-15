# XLink：XLink 实例

- 来源：[XLink 实例](https://www.runoob.com/xlink/xlink-example.html)
- 分类：XML / Web Service
- 技术：XLink
- 笔记类型：练习笔记
- 章节序号：4368

## 本章内容

让我们通过研究一个实例来学习一些基础的 XLink 语法。


## XML 实例文档

请看下面的 XML 文档，"bookstore.xml"，它用来呈现书籍：

在您的浏览器查看 "bookstore.xml" bookstore.xml文件。

在上面的例子中，XLink 文档命名空间(xmlns:xlink="http://www.w3.org/1999/xlink")被声明于文档的顶部。 这意味着文档可访问 XLink 的属性和特性。

xlink:type="simple" 可创建简单的类似 HTML 的链接。您也可以规定更多的复杂的链接（多方向链接），但是目前，我们仅使用简易链接。

xlink:href 属性规定了要链接的 URL，而 xlink:show 属性规定了在何处打开链接。xlink:show="new" 意味着链接（在此例中，是一幅图像）会在新窗口打开。


## XLink - 深入学习

在上面的例子中，我们只展示了简单的链接。当我们要访问远程位置的资源，而不是独立的页面时，XLink是变得更有趣。在上面的例子<description>元素集的XLINK属性显示的值为："new"。这意味着，应该在新窗口打开链接。我们可以设置XLINK中的值：显示属性"embed"。这意味着资源应嵌入到页面处理。你认为这可能是另一个XML文档，而不是只是一个图像，你可以建立一个XML文档中层次结构的例子。

使用XLink，你还可以指定资源时才显示。这是由XLink的actuate属性处理。XLINK：actuate"="onLoad"指定的资源文件应加载和显示。XLINK：actuate="onRequest"意味着链接被点击之前无法读取或显示资源。这对低带宽设置非常方便。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XLink 实例` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
