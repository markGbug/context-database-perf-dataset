# JavaScript：JavaScript 计时事件

- 来源：[JavaScript 计时事件](https://www.runoob.com/js/js-timing.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2828

## 本章内容

JavaScript 一个设定的时间间隔之后来执行代码

我们称之为计时事件


## JavaScript 计时事件

通过使用 JavaScript，我们有能力做到在一个设定的时间间隔之后来执行代码，而不是在函数被调用后立即执行。我们称之为计时事件。

在 JavaScript 中使用计时事件是很容易的，两个关键方法是:

- setInterval() - 间隔指定的毫秒数不停地执行指定的代码。
- setTimeout() - 在指定的毫秒数后执行指定代码。

注意: setInterval() 和 setTimeout() 是 HTML DOM Window对象的两个方法。


## setInterval() 方法

setInterval() 间隔指定的毫秒数不停地执行指定的代码


### 语法

window.setInterval() 方法可以不使用 window 前缀，直接使用函数 setInterval()。

setInterval() 第一个参数是函数（function）。

第二个参数间隔的毫秒数

注意: 1000 毫秒是一秒。


## 实例

每三秒弹出 "hello" ：

```text
setInterval(function(){alert("Hello")},3000);
```

实例展示了如何使用 setInterval() 方法，但是每三秒弹出一次对用户体验并不好。

以下实例将显示当前时间。 setInterval() 方法设置每秒钟执行一次代码，就是手表一样。


## 实例

显示当前时间

```javascript
var myVar=setInterval(function(){myTimer()},1000);

function myTimer()
{
    var d=new Date();
    var t=d.toLocaleTimeString();
    document.getElementById("demo").innerHTML=t;
}
```


## 如何停止执行?

clearInterval() 方法用于停止 setInterval() 方法执行的函数代码。


### 语法

window.clearInterval() 方法可以不使用window前缀，直接使用函数clearInterval()。

要使用 clearInterval() 方法, 在创建计时方法时你必须使用全局变量：

然后你可以使用 clearInterval() 方法来停止执行。


## 实例

以下例子,我们添加了 "停止" 按钮：

```html
<p id="demo"></p>
<button onclick="myStopFunction()">停止</button>
<script>
var myVar=setInterval(function(){myTimer()},1000);
function myTimer(){
    var d=new Date();
    var t=d.toLocaleTimeString();
    document.getElementById("demo").innerHTML=t;
}
function myStopFunction(){
    clearInterval(myVar);
}
</script>
```


## setTimeout() 方法


### 语法

setTimeout() 方法会返回某个值。在上面的语句中，值被储存在名为 myVar 的变量中。假如你希望取消这个 setTimeout()，你可以使用这个变量名来指定它。

setTimeout() 的第一个参数是含有 JavaScript 语句的字符串。这个语句可能诸如 "alert('5 seconds!')"，或者对函数的调用，诸如 alertMsg。

第二个参数指示从当前起多少毫秒后执行第一个参数。

提示：1000 毫秒等于一秒。


## 实例

等待3秒，然后弹出 "Hello":

```text
setTimeout(function(){alert("Hello")},3000);
```


## 如何停止执行?

clearTimeout() 方法用于停止执行setTimeout()方法的函数代码。


### 语法

window.clearTimeout() 方法可以不使用window 前缀。

要使用clearTimeout() 方法, 你必须在创建超时方法中（setTimeout）使用全局变量:

如果函数还未被执行，你可以使用 clearTimeout() 方法来停止执行函数代码。


## 实例

以下是同一个实例, 但是添加了 "Stop the alert" 按钮:

```javascript
var myVar;

function myFunction()
{
    myVar=setTimeout(function(){alert("Hello")},3000);
}

function myStopFunction()
{
    clearTimeout(myVar);
}
```


## 更多实例

另一个简单的计时


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript 计时事件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
