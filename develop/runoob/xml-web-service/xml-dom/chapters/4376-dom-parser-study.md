# XML DOM：XML DOM 解析器

- 来源：[DOM 解析](https://www.runoob.com/dom/dom-parser.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4376

## 本章内容

大多数浏览器都内建了供读取和操作 XML 的 XML 解析器。

解析器把 XML 转换为 JavaScript 可存取的对象（XML DOM）。


## XML 解析器

XML DOM 包含了遍历 XML 树，访问、插入及删除节点的方法（函数）。

然而，在访问和操作 XML 文档之前，它必须加载到 XML DOM 对象。

XML 解析器读取 XML，并把它转换为 XML DOM 对象，这样才可以使用 JavaScript 访问它。

大多数浏览器有一个内建的 XML 解析器。


## 加载 XML 文档

下面的 JavaScript 片段加载一个 XML 文档（"books.xml"）：


## 实例

```text
if (window.XMLHttpRequest)
{
  // IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
  xhttp=new XMLHttpRequest();
}
else
{
  // IE6, IE5 浏览器执行代码
  xhttp=new ActiveXObject("Microsoft.XMLHTTP");
}
xhttp.open("GET","books.xml",false);
xhttp.send();
xmlDoc=xhttp.responseXML;
```

代码解释：

- 创建一个 XMLHTTP 对象
- 打开 XMLHTTP 对象
- 发送一个 XML HTTP 请求到服务器
- 设置响应为 XML DOM 对象


## 加载 XML 字符串

下面的代码加载并解析一个 XML 字符串：


## 实例

```text
if (window.DOMParser)
{
  parser=new DOMParser();
  xmlDoc=parser.parseFromString(text,"text/xml");
}
else
{
   // Internet Explorer
  xmlDoc=new ActiveXObject("Microsoft.XMLDOM");
  xmlDoc.async=false;
  xmlDoc.loadXML(text);
}
```

注意：Internet Explorer 使用 loadXML() 方法来解析 XML 字符串，而其他浏览器使用 DOMParser 对象。


## 跨域访问

出于安全原因，现代的浏览器不允许跨域访问。

这意味着，网页以及 XML 文件，它必须位于同一台服务器上尝试加载。

菜鸟教程上的实例中所有打开的 XML 文件都是位于菜鸟教程域上的。

如果您想要在您的网页上使用上面的实例，您加载的 XML 文件必须位于您自己的服务器上。


## 复习重点

- 能说明 `DOM 解析` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
