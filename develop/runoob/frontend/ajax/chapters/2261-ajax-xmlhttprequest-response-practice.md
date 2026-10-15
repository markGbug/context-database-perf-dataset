# AJAX：AJAX - 服务器 响应

- 来源：[XHR 响应](https://www.runoob.com/ajax/ajax-xmlhttprequest-response.html)
- 分类：前端开发
- 技术：AJAX
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XHR 响应` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
