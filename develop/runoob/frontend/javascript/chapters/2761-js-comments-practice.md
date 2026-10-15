# JavaScript：JavaScript 注释

- 来源：[JavaScript 注释](https://www.runoob.com/js/js-comments.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2761

## 本章内容

JavaScript 注释可用于提高代码的可读性。


## JavaScript 注释

JavaScript 不会执行注释。

我们可以添加注释来对 JavaScript 进行解释，或者提高代码的可读性。

单行注释以 // 开头。

本例用单行注释来解释代码：


## 实例

```text
// 输出标题：
document.getElementById("myH1").innerHTML="欢迎来到我的主页";
// 输出段落：
document.getElementById("myP").innerHTML="这是我的第一个段落。";
```


## JavaScript 多行注释

多行注释以 /* 开始，以 */ 结尾。

下面的例子使用多行注释来解释代码：


## 实例

```text
/*
下面的这些代码会输出
一个标题和一个段落
并将代表主页的开始
*/
document.getElementById("myH1").innerHTML="欢迎来到我的主页";
document.getElementById("myP").innerHTML="这是我的第一个段落。";
```


## 使用注释来阻止执行

在下面的例子中，注释用于阻止其中一条代码行的执行（可用于调试）：


## 实例

```text
// document.getElementById("myH1").innerHTML="欢迎来到我的主页";
document.getElementById("myP").innerHTML="这是我的第一个段落。";
```

在下面的例子中，注释用于阻止代码块的执行（可用于调试）：


## 实例

```text
/*
document.getElementById("myH1").innerHTML="欢迎来到我的主页";
document.getElementById("myP").innerHTML="这是我的第一个段落。";
*/
```


## 在行末使用注释

在下面的例子中，我们把注释放到代码行的结尾处：


## 实例

```javascript
var x=5;    // 声明 x 并把 5 赋值给它
var y=x+2;  // 声明 y 并把 x+2 赋值给它
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript 注释` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
