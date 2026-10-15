# AngularJS：AngularJS 应用

- 来源：[AngularJS 应用](https://www.runoob.com/angularjs/angularjs-application.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：学习笔记
- 章节序号：2301

## 本章内容

现在是时候创建一个真正的 AngularJS 单页 Web 应用（single page web application，SPA）了。


## AngularJS 应用实例

您已经学习了足够多关于 AngularJS 的知识，现在可以开始创建您的第一个 AngularJS 应用程序：


## 我的笔记

剩余字数: 100


## 应用程序讲解


## AngularJS 实例

应用程序文件 "myNoteApp.js":

控制器文件 "myNoteCtrl.js":

<html> 元素是 AngularJS 应用: ng-app="myNoteApp" 的容器:

<div> 是 HTML 页面中控制器: ng-controller="myNoteCtrl" 的作用域:

ng-model 指令绑定了 <textarea> 到控制器变量 message:

两个 ng-click 事件调用了控制器函数 clear() 和 save():

ng-bind 指令绑定控制器函数 left() 到<span> ，用于显示剩余字符:

应用库文件需要在 AngularJs 加载后才能执行：


## AngularJS 应用架构

以上实例是一个完整的 AngularJS 单页Web应用（single page web application，SPA）。

<html> 元素包含了 AngularJS 应用 (ng-app=)。

<div> 元素定义了 AngularJS 控制器的作用域 (ng-controller=)。

在一个应用可以有很多控制器。

应用文件(my...App.js) 定义了应用模型代码。

一个或多个控制器文件 (my...Ctrl.js) 定义了控制器代码。


## 总结 - 它是如何工作的呢？

ng-app 指令位于应用的根元素下。

对于单页Web应用（single page web application，SPA），应用的根通常为 <html> 元素。

一个或多个 ng-controller 指令定义了应用的控制器。每个控制器有他自己的作用域：: 定义的 HTML 元素。

AngularJS 在 HTML DOMContentLoaded 事件中自动开始。如果找到 ng-app 指令 ， AngularJS 载入指令中的模块，并将 ng-app 作为应用的根进行编译。

应用的根可以是整个页面，或者页面的一小部分，如果是一小部分会更快编译和执行。


## 复习重点

- 能说明 `AngularJS 应用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
