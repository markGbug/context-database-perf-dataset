# AJAX：AJAX XML 实例

- 来源：[AJAX XML](https://www.runoob.com/ajax/ajax-xmlfile.html)
- 分类：前端开发
- 技术：AJAX
- 笔记类型：学习笔记
- 章节序号：2265

## 本章内容

AJAX 可用来与 XML 文件进行交互式通信。


## AJAX XML 实例

下面的例子将演示网页如何使用 AJAX 来读取来自 XML 文件的信息：


## 实例


## 实例解析 - loadXMLDoc() 函数

当用户点击上面的"获取我收藏的 CD"这个按钮，就会执行 loadXMLDoc() 函数。

loadXMLDoc() 函数创建 XMLHttpRequest 对象，添加当服务器响应就绪时执行的函数，并将请求发送到服务器。

当服务器响应就绪时，会构建一个 HTML 表格，从 XML 文件中提取节点（元素），最后使用 XML 数据的 填充 id="demo" 的表格元素：


## 异步加载 XML 文档

```java
function loadXMLDoc() {
  var xhttp = new XMLHttpRequest();
  xhttp.onreadystatechange = function() {
    if (this.readyState == 4 && this.status == 200) {
    myFunction(this);
    }
  };
  xhttp.open("GET", "cd_catalog.xml", true);
  xhttp.send();
}
function myFunction(xml) {
  var i;
  var xmlDoc = xml.responseXML;
  var table="<tr><th>Artist</th><th>Title</th></tr>";
  var x = xmlDoc.getElementsByTagName("CD");
  for (i = 0; i <x.length; i++) {
    table += "<tr><td>" +
    x[i].getElementsByTagName("ARTIST")[0].childNodes[0].nodeValue +
    "</td><td>" +
    x[i].getElementsByTagName("TITLE")[0].childNodes[0].nodeValue +
    "</td></tr>";
  }
  document.getElementById("demo").innerHTML = table;
}
```


## AJAX 服务器页面

上面这个例子中使用的服务器页面实际上是一个名为 "cd_catalog.xml" XML 文件。


## 复习重点

- 能说明 `AJAX XML` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
