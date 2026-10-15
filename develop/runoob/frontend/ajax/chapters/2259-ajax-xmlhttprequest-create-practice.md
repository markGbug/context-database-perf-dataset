# AJAX：AJAX - 创建 XMLHttpRequest 对象

- 来源：[XHR 创建对象](https://www.runoob.com/ajax/ajax-xmlhttprequest-create.html)
- 分类：前端开发
- 技术：AJAX
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XHR 创建对象` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
