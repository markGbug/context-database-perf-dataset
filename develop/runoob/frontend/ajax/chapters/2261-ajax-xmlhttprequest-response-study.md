# AJAX：AJAX - 服务器 响应

- 来源：[XHR 响应](https://www.runoob.com/ajax/ajax-xmlhttprequest-response.html)
- 分类：前端开发
- 技术：AJAX
- 笔记类型：学习笔记
- 章节序号：2261

## 本章内容

## 服务器响应

如需获得来自服务器的响应，请使用 XMLHttpRequest 对象的 responseText 或 responseXML 属性。


## responseText 属性

如果来自服务器的响应并非 XML，请使用 responseText 属性。

responseText 属性返回字符串形式的响应，因此您可以这样使用：


## 实例


## responseXML 属性

如果来自服务器的响应是 XML，而且需要作为 XML 对象进行解析，请使用 responseXML 属性：


## 实例

请求 cd_catalog.xml 文件，并解析响应：

```java
xmlDoc=xmlhttp.responseXML;
txt="";
x=xmlDoc.getElementsByTagName("ARTIST");
for (i=0;i<x.length;i++)
{
    txt=txt + x[i].childNodes[0].nodeValue + "<br>";
}
document.getElementById("myDiv").innerHTML=txt;
```


## 复习重点

- 能说明 `XHR 响应` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
