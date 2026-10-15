# XML DOM：XMLHttpRequest 对象

- 来源：[DOM XMLHttpRequest](https://www.runoob.com/dom/dom-httprequest.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：练习笔记
- 章节序号：4392

## 本章内容

通过 XMLHttpRequest 对象，您可以在不重新加载整个页面的情况下更新网页中的某个部分。


## XMLHttpRequest 对象

XMLHttpRequest 对象用于幕后与服务器交换数据。

XMLHttpRequest 对象是开发者的梦想，因为您可以：

- 在不重新加载页面的情况下更新网页
- 在页面已加载后从服务器请求数据
- 在页面已加载后从服务器接收数据
- 在后台向服务器发送数据


## 创建 XMLHttpRequest 对象

所有现代的浏览器（IE7+、Firefox、Chrome、Safari 和 Opera）都有一个内建的 XMLHttpRequest 对象。

创建 XMLHttpRequest 对象的语法

旧版本的 Internet Explorer（IE5 和 IE6）使用 ActiveX 对象：

为了处理所有现代的浏览器，包括 IE5 和 IE6，请检查浏览器是否支持 XMLHttpRequest 对象。如果支持，则创建一个 XMLHttpRequest 对象，如果不支持，则创建一个 ActiveX 对象：


## 实例

```text
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
```


## 发送一个请求到服务器

为了发送一个请求到服务器，我们使用 XMLHttpRequest 对象的 open() 和 send() 方法：


## GET 或 POST？

GET 比 POST 简单并且快速，可用于大多数情况下。

然而，下面的情况下请始终使用 POST 请求：

- 缓存的文件不是一个选项（更新服务器上的文件或数据库）
- 发送到服务器的数据量较大（POST 没有大小的限制）
- 发送用户输入（可以包含未知字符），POST 比 GET 更强大更安全


## URL - 服务器上的文件

open() 方法的 url 参数，是一个在服务器上的文件的地址：

该文件可以是任何类型的文件（如 .txt 和 .xml），或服务器脚本文件（如.html 和 .php，可在发送回响应之前在服务器上执行动作）。


## 异步 - True 或 False?

如需异步发送请求，open() 方法的 async 参数必需设置为 true：

发送异步请求对于 Web 开发人员是一个巨大的进步。在服务器上执行的许多任务非常费时。

通过异步发送，JavaScript 不需要等待服务器的响应，但可以替换为：

- 等待服务器的响应时，执行其他脚本
- 响应准备时处理响应


## Async=true

当使用 async=true 时，在 onreadystatechange 事件中响应准备时规定一个要执行的函数：


## 实例

```text
xmlhttp.onreadystatechange=function()
{
  if (xmlhttp.readyState==4 && xmlhttp.status==200)
  {
    document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
  }
}
xmlhttp.open("GET","xmlhttp_info.txt",true);
xmlhttp.send();
```


## Async=false

如需使用 async=false，请更改 open() 方法的第三个参数为 false：

不推荐使用 async=false，但如果处理几个小的请求还是可以的。

请记住，JavaScript 在服务器响应准备之前不会继续执行。如果服务器正忙或缓慢，应用程序将挂起或停止。

注意：当您使用 async=false 时，不要编写 onreadystatechange 函数 - 只需要把代码放置在 send() 语句之后即可：


## 实例

```text
xmlhttp.open("GET","xmlhttp_info.txt",false);
xmlhttp.send();
document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
```


## 服务器响应

如需从服务器获取响应，请使用 XMLHttpRequest 对象的 responseText 或 responseXML 属性。


## responseText 属性

如果来自服务器的响应不是 XML，请使用 responseText 属性。

responseText 属性以字符串形式返回响应，您可以相应地使用它：


## 实例

```text
document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
```


## responseXML 属性

如果来自服务器的响应是 XML，且您想要把它解析为 XML 对象，请使用 responseXML 属性：


## 实例

请求文件 cd_catalog.xml 并解析响应：

```java
xmlDoc=xmlhttp.responseXML;
var txt="";
x=xmlDoc.getElementsByTagName("ARTIST");
for (i=0;i<x.length;i++)
{
  txt=txt + x[i].childNodes[0].nodeValue + "";
}
document.getElementById("myDiv").innerHTML=txt;
```


## onreadystatechange 事件

当请求被发送到服务器，我们要根据响应执行某些动作。

onreadystatechange 事件在每次 readyState 变化时被触发。

readyState 属性持有 XMLHttpRequest 的状态。

XMLHttpRequest 对象的三个重要的属性：

在 onreadystatechange 事件中，我们规定当服务器的响应准备处理时会发生什么。

当 readyState 是 4 或状态是 200 时，响应准备：


## 实例

```text
xmlhttp.onreadystatechange=function()
{
  if (xmlhttp.readyState==4 && xmlhttp.status==200)
  {
    document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
  }
}
```

注意：onreadystatechange 事件在每次 readyState 发生变化时被触发，总共触发了四次。


## 更多实例

通过 getAllResponseHeaders() 检索头信息 检索资源（文件）的头信息。

通过 getResponseHeader() 检索指定头信息 检索资源（文件）的指定头信息。

检索 ASP 文件的内容 当用户在输入字段键入字符时，网页如何与 Web 服务器进行通信。

从数据库中检索内容 网页如何通过 XMLHttpRequest 对象从数据库中提取信息。

检索 XML 文件的内容 创建一个 XMLHttpRequest 从 XML 文件中检索数据并把数据显示在一个 HTML 表格中。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM XMLHttpRequest` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
