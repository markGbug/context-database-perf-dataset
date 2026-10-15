# XML：XML 注意事项

- 来源：[XML 注意事项](https://www.runoob.com/xml/xml-dont.html)
- 分类：XML / Web Service
- 技术：XML
- 笔记类型：学习笔记
- 章节序号：4459

## 本章内容

这里列出了您在使用 XML 时应该尽量避免使用的技术。


## Internet Explorer - XML 数据岛

它是什么？XML 数据岛是嵌入到 HTML 页面中的 XML 数据。

为什么要避免使用它？XML 数据岛只在 Internet Explorer 浏览器中有效。

用什么代替它？您应当在 HTML 中使用 JavaScript 和 XML DOM 来解析并显示 XML。

如需更多有关 JavaScript 和 XML DOM 的信息，请访问我们的 XML DOM 教程。


## XML 数据岛实例

本例使用 XML 文档 "cd_catalog.xml"。

把 XML 文档绑定到 HTML 文档中的一个 <xml> 标签。id 属性定义数据岛的标识符，而 src 属性指向 XML 文件：


## 实例

本实例只适用于 IE 浏览器

<table> 标签的 datasrc 属性把 HTML 表格绑定到 XML 数据岛。

<span> 标签允许 datafld 属性引用要显示的 XML 元素。在这个实例中，要引用的是 "ARTIST" 和 "TITLE"。当读取 XML 时，会为每个 <CD> 元素创建相应的表格行。


## Internet Explorer - 行为

它是什么？Internet Explorer 5 引入了行为。行为是通过使用 CSS 样式向 XML （或 HTML ）元素添加行为的一种方法。

为什么要避免使用它？只有 Internet Explorer 支持 behavior 属性。

使用什么代替它？使用 JavaScript 和 XML DOM（或 HTML DOM）来代替它。


## 实例 1 - 鼠标悬停突出

下面的 HTML 文件中的 <style> 元素为 <h1> 元素定义了一个行为：

下面显示的是 XML 文档 "behave.htc"（该文件包含了一段 JavaScript 和针对元素的事件句柄）：


## 实例 2 - 打字机模拟

下面的 HTML 文件中的 <style> 元素为 id 为 "typing" 的元素定义了一个行为：

下面显示的是 XML 文档 "typing.htc"：


## 复习重点

- 能说明 `XML 注意事项` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
