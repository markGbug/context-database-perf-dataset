# AJAX：AJAX - 创建 XMLHttpRequest 对象

- 来源：[XHR 创建对象](https://www.runoob.com/ajax/ajax-xmlhttprequest-create.html)
- 分类：前端开发
- 技术：AJAX
- 笔记类型：学习笔记
- 章节序号：2259

## 本章内容

XMLHttpRequest 是 AJAX 的基础。


## XMLHttpRequest 对象

所有现代浏览器均支持 XMLHttpRequest 对象（IE5 和 IE6 使用 ActiveXObject）。

XMLHttpRequest 用于在后台与服务器交换数据。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新。


## 创建 XMLHttpRequest 对象

所有现代浏览器（IE7+、Edge、Firefox、Chrome、Safari 以及 Opera）均内建 XMLHttpRequest 对象。

创建 XMLHttpRequest 对象的语法：

```javascript
var xhr = new XMLHttpRequest();
```

老版本的 Internet Explorer （IE5 和 IE6）使用 ActiveX 对象：

```javascript
var xhr = new ActiveXObject("Microsoft.XMLHTTP");
```

为了应对所有的现代浏览器，包括 IE5 和 IE6（现在应该很少人使用了），请检查浏览器是否支持 XMLHttpRequest 对象。如果支持，则创建 XMLHttpRequest 对象。如果不支持，则创建 ActiveXObject ：


## 实例

```javascript
var xmlhttp;
if (window.XMLHttpRequest) {
    //  IE7+, Firefox, Chrome, Opera, Safari 浏览器执行代码
    xmlhttp=new XMLHttpRequest();
} else {
    // IE6, IE5 浏览器执行代码
    xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
}
```

创建一个 XMLHttpRequest 对象的示例：


## 实例

在下一章中，您将学习发送服务器请求的知识。


## 复习重点

- 能说明 `XHR 创建对象` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
