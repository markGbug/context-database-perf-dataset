# XML DOM：XML DOM 加载函数

- 来源：[DOM 加载函数](https://www.runoob.com/dom/dom-loadxmldoc.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4377

## 本章内容

加载 XML 文档中的代码可以存储在一个函数中。


## loadXMLDoc() 函数

为了使前一页中的代码易于维护（检查旧的浏览器），它应该写成一个函数：


## loadxmldoc.js 文件代码：

```javascript
function loadXMLDoc(dname)
{
    if (window.XMLHttpRequest)
    {
        xhttp=new XMLHttpRequest();
    }
    else
    {
        xhttp=new ActiveXObject("Microsoft.XMLHTTP");
    }
    xhttp.open("GET",dname,false);
    xhttp.send();
    return xhttp.responseXML;
}
```

上面的函数可以存储在 HTML 页面的 <head> 部分，并从页面中的脚本调用。

上面描述的函数，用于本教程中所有 XML 文档实例！


## loadXMLDoc() 的外部 JavaScript

为了使上述代码更容易维护，以确保在所有页面中使用相同的代码，我们把函数存储在一个外部文件中。

文件名为 "loadxmldoc.js"，且在 HTML 页面中的 head 部分被加载。然后，页面中的脚本调用 loadXMLDoc() 函数。

下面的实例使用 loadXMLDoc() 函数加载 books.xml：


## 实例

```html
<html>
<head>
<script src="loadxmldoc.js">
</script>
</head>
<body>

<script>
xmlDoc=loadXMLDoc("books.xml");

code goes here.....

</script>

</body>
</html>
```

如何从 XML 文件中获得数据，将在下一章中讲解。


## loadXMLString() 函数

为了使前一页中的代码易于维护（检查旧的浏览器），它应该写成一个函数：


## loadxmlstring.js 文件代码：

```javascript
function loadXMLString(txt)
{
    if (window.DOMParser)
    {
        parser=new DOMParser();
        xmlDoc=parser.parseFromString(txt,"text/xml");
    }
    else
    {
        // Internet Explorer
        xmlDoc=new ActiveXObject("Microsoft.XMLDOM");
        xmlDoc.async=false;
        xmlDoc.loadXML(txt);
    }
    return xmlDoc;
}
```

上面的函数可以存储在 HTML 页面的 <head> 部分，并从页面中的脚本调用。

上面描述的函数，用于本教程中所有 XML 字符串实例！


## loadXMLString() 的外部 JavaScript

我们已经把 loadXMLString() 函数存储在名为 "loadxmlstring.js" 文件中。


## 实例

```html
<html>
<head>
<script src="loadxmlstring.js"></script>
</head>
<body>
<script>
```

```html
text="<bookstore>"
text=text+"<book>";
text=text+"<title>Everyday Italian</title>";
text=text+"<author>Giada De Laurentiis</author>";
text=text+"<year>2005</year>";
text=text+"</book>";
text=text+"</bookstore>";

xmlDoc=loadXMLString(text);

code goes here.....
```

```text
</script>
</body>
</html>
```


## 复习重点

- 能说明 `DOM 加载函数` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
