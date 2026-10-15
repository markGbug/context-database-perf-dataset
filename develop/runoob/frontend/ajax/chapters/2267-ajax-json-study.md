# AJAX：AJAX JSON 实例

- 来源：[AJAX JSON 实例](https://www.runoob.com/ajax/ajax-json.html)
- 分类：前端开发
- 技术：AJAX
- 笔记类型：学习笔记
- 章节序号：2267

## 本章内容

AJAX 可用来与 JSON 文件进行交互式通信。


## AJAX JSON 实例

下面的例子将演示网页如何使用 AJAX 来读取来自 JSON 文件的信息：


## 实例


## 实例解析 - loadXMLDoc() 函数

当用户点击上面的"获取课程数据"这个按钮，就会执行 loadXMLDoc() 函数。

loadXMLDoc() 函数创建 XMLHttpRequest 对象，添加当服务器响应就绪时执行的函数，并将请求发送到服务器。

当服务器响应就绪时，我们就使用 JSON.parse() 方法将数据转换为 JavaScript 对象。：


## 异步加载 JSON 文档

```java
function loadXMLDoc()
{
  var xmlhttp;
  if (window.XMLHttpRequest)
  {
    // IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
    xmlhttp=new XMLHttpRequest();
  }
  else
  {
    // IE6, IE5 浏览器执行代码
    xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
  }
  xmlhttp.onreadystatechange=function()
  {
    if (xmlhttp.readyState==4 && xmlhttp.status==200)
    {
      var myArr = JSON.parse(this.responseText);
      myFunction(myArr)
    }
  }
  xmlhttp.open("GET","/try/ajax/json_ajax.json",true);
  xmlhttp.setRequestHeader("Content-Type", "application/json;charset=UTF-8");
  xmlhttp.send();
}
function myFunction(arr) {
  var out = "";
  var i;
  for(i = 0; i < arr.length; i++) {
    out += '<a href="' + arr[i].url + '">' +
    arr[i].title + '</a><br>';
  }
 document.getElementById("myDiv").innerHTML=out;
}
```


## AJAX 服务器页面

上面这个例子中使用的服务器页面实际上是一个名为 "json_ajax.json" JSON 文件。

JSON 数据如下：


## json_ajax.json 文件：

```text
[
  {
    "title": "JavaScript 教程",
    "url": "https://www.runoob.com/js/"
  },
  {
    "title": "HTML 教程",
    "url": "https://www.runoob.com/html/"
  },
  {
    "title": "CSS 教程",
    "url": "https://www.runoob.com/css/"
  }
]
```

发送 JSON 数据：

```text
xmlhttp.send(JSON.stringify({ "email": "admin@runoob.com", "response": { "name": "runoob" } }));
```


## 复习重点

- 能说明 `AJAX JSON 实例` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
