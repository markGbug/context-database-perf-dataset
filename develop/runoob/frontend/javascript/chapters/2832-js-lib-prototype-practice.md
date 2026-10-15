# JavaScript：JavaScript - 测试 Prototype

- 来源：[JavaScript 测试 Prototype](https://www.runoob.com/js/js-lib-prototype.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2832

## 本章内容

测试 JavaScript 框架库 - Prototype


## 引用 Prototype

如需测试 JavaScript 库，您需要在网页中引用它。

为了引用某个库，请使用 <script> 标签，其 src 属性设置为库的 URL：


## 引用 Prototype

```html
<!DOCTYPE html>
<html>
<head>
<script
src="https://cdn.staticfile.org/prototype/1.7.3/prototype.min.js">
</script>
</head>
<body>
</body>
</html>
```


## Prototype 描述

Prototype 提供的函数可使 HTML DOM 编程更容易。

与 jQuery 类似，Prototype 也有自己的 $() 函数。

$() 函数接受 HTML DOM 元素的 id 值（或 DOM 元素），并会向 DOM 对象添加新的功能。

与 jQuery 不同，Prototype 没有用以取代 window.onload() 的 ready() 方法。相反，Prototype 会向浏览器及 HTML DOM 添加扩展。

在 JavaScript 中，您可以分配一个函数以处理窗口加载事件：


## JavaScript 方式：

```javascript
function myFunction()
{
    var obj=document.getElementById("h01");
    obj.innerHTML="Hello Prototype";
}
onload=myFunction;
```

等价的 Prototype 是不同的：


## Prototype 方式：

```javascript
function myFunction()
{
    $("h01").insert("Hello Prototype!");
}
Event.observe(window,"load",myFunction);
```

Event.observe() 接受三个参数：

- 您希望处理的 HTML DOM 或 BOM（浏览器对象模型）对象
- 您希望处理的事件
- 您希望调用的函数


## 测试 Prototype

请试一下下面这个例子：


## Example

```html
<!DOCTYPE html>
<html>
<script src="https://cdn.staticfile.org/prototype/1.7.3/prototype.min.js">
</script>
<script>
function myFunction()
{
    $("h01").insert("Hello Prototype!");
}
Event.observe(window,"load",myFunction);
</script>
</head>
<body>
<h1 id="h01"></h1>
</body>
</html>
```

请再试一下这个例子：


## Example

```html
<!DOCTYPE html>
<html>
<script src="https://cdn.staticfile.org/prototype/1.7.3/prototype.min.js">
</script>
<script>
function myFunction()
{
    $("h01").writeAttribute("style","color:red").insert("Hello Prototype!");
}
Event.observe(window,"load",myFunction);
</script>
</head>
<body>
<h1 id="h01"></h1>
</body>
</html>
```

正如您在上面的例子中看到的，与 jQuery 相同，Prototype 允许链式语法。

链接（Chaining）是一种在同一对象上执行多个任务的便捷方法。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript 测试 Prototype` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
