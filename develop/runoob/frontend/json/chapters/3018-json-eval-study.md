# JSON：JSON 使用

- 来源：[JSON 使用](https://www.runoob.com/json/json-eval.html)
- 分类：前端开发
- 技术：JSON
- 笔记类型：学习笔记
- 章节序号：3018

## 本章内容

## 把 JSON 文本转换为 JavaScript 对象

JSON 最常见的用法之一，是从 web 服务器上读取 JSON 数据（作为文件或作为 HttpRequest），将 JSON 数据转换为 JavaScript 对象，然后在网页中使用该数据。

为了更简单地为您讲解，我们使用字符串作为输入进行演示（而不是文件）。


## JSON 实例 - 来自字符串的对象

创建包含 JSON 语法的 JavaScript 字符串：

```javascript
var txt = '{ "sites" : [' +
'{ "name":"菜鸟教程" , "url":"www.runoob.com" },' +
'{ "name":"google" , "url":"www.google.com" },' +
'{ "name":"微博" , "url":"www.weibo.com" } ]}';
```

由于 JSON 语法是 JavaScript 语法的子集，JavaScript 函数 eval() 可用于将 JSON 文本转换为 JavaScript 对象。

eval() 函数使用的是 JavaScript 编译器，可解析 JSON 文本，然后生成 JavaScript 对象。必须把文本包围在括号中，这样才能避免语法错误：

在网页中使用 JavaScript 对象：


## 实例

```javascript
var txt = '{ "sites" : [' +
'{ "name":"菜鸟教程" , "url":"www.runoob.com" },' +
'{ "name":"google" , "url":"www.google.com" },' +
'{ "name":"微博" , "url":"www.weibo.com" } ]}';

var obj = eval ("(" + txt + ")");

document.getElementById("name").innerHTML=obj.sites[0].name
document.getElementById("url").innerHTML=obj.sites[0].url
```


## JSON 解析器

eval() 函数可编译并执行任何 JavaScript 代码。这隐藏了一个潜在的安全问题。

使用 JSON 解析器将 JSON 转换为 JavaScript 对象是更安全的做法。JSON 解析器只能识别 JSON 文本，而不会编译脚本。

在浏览器中，这提供了原生的 JSON 支持，而且 JSON 解析器的速度更快。

较新的浏览器和最新的 ECMAScript (JavaScript) 标准中均包含了原生的对 JSON 的支持。

- Firefox (Mozilla) 3.5
- Internet Explorer 8
- Chrome
- Opera 10
- Safari 4
- jQuery
- Yahoo UI
- Prototype
- Dojo
- ECMAScript 1.5

尝试一下 »

对于较老的浏览器，可使用 JavaScript 库： https://github.com/douglascrockford/JSON-js

JSON 格式最初是 originally specified by Douglas Crockford


## 复习重点

- 能说明 `JSON 使用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
