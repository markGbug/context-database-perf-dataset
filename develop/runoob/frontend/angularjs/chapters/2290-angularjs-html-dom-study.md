# AngularJS：AngularJS HTML DOM

- 来源：[AngularJS HTML DOM](https://www.runoob.com/angularjs/angularjs-html-dom.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：学习笔记
- 章节序号：2290

## 本章内容

AngularJS 为 HTML DOM 元素的属性提供了绑定应用数据的指令。


## ng-disabled 指令

ng-disabled 指令直接绑定应用程序数据到 HTML 的 disabled 属性。


## AngularJS 实例

实例讲解：

ng-disabled 指令绑定应用程序数据 "mySwitch" 到 HTML 的 disabled 属性。

ng-model 指令绑定 "mySwitch" 到 HTML input checkbox 元素的内容（value）。

如果 mySwitch 为true, 按钮将不可用:

如果 mySwitch 为false, 按钮则可用:


## ng-show 指令

ng-show 指令隐藏或显示一个 HTML 元素。


## AngularJS 实例

ng-show 指令根据 value 的值来显示（隐藏）HTML 元素。

你可以使用表达式来计算布尔值（ true 或 false）:


## AngularJS 实例

```html
<div ng-app="" ng-init="hour=13">

<p ng-show="hour > 12">我是可见的。</p>

</div>
```


## ng-hide 指令

ng-hide 指令用于隐藏或显示 HTML 元素。


## AngularJS 实例


## 复习重点

- 能说明 `AngularJS HTML DOM` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
