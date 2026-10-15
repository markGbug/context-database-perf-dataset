# AngularJS：AngularJS 表达式

- 来源：[AngularJS 表达式](https://www.runoob.com/angularjs/angularjs-expressions.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：学习笔记
- 章节序号：2279

## 本章内容

AngularJS 使用 表达式 把数据绑定到 HTML。


## AngularJS 表达式

AngularJS 表达式写在双大括号内：{{ expression }}。

AngularJS 表达式把数据绑定到 HTML，这与 ng-bind 指令有异曲同工之妙。

AngularJS 将在表达式书写的位置"输出"数据。

AngularJS 表达式 很像 JavaScript 表达式：它们可以包含文字、运算符和变量。

实例 {{ 5 + 5 }} 或 {{ firstName + " " + lastName }}


## AngularJS 实例

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<script src="http://cdn.static.runoob.com/libs/angular.js/1.4.6/angular.min.js"></script>
</head>
<body>

<div ng-app="">
     <p>我的第一个表达式: {{ 5 + 5 }}</p>
</div>

</body>
</html>
```


## AngularJS 数字

AngularJS 数字就像 JavaScript 数字：


## AngularJS 实例

```html
<div ng-app="" ng-init="quantity=1;cost=5">

<p>总价： {{ quantity * cost }}</p>

</div>
```

使用 ng-bind 的相同实例：


## AngularJS 实例

```html
<div ng-app="" ng-init="quantity=1;cost=5">

<p>总价： <span ng-bind="quantity * cost"></span></p>

</div>
```


## AngularJS 字符串

AngularJS 字符串就像 JavaScript 字符串：


## AngularJS 实例

```html
<div ng-app="" ng-init="firstName='John';lastName='Doe'">

<p>姓名： {{ firstName + " " + lastName }}</p>

</div>
```

使用 ng-bind 的相同实例：


## AngularJS 实例

```html
<div ng-app="" ng-init="firstName='John';lastName='Doe'">

<p>姓名： <span ng-bind="firstName + ' ' + lastName"></span></p>

</div>
```


## AngularJS 对象

AngularJS 对象就像 JavaScript 对象：


## AngularJS 实例

```html
<div ng-app="" ng-init="person={firstName:'John',lastName:'Doe'}">

<p>姓为 {{ person.lastName }}</p>

</div>
```

使用 ng-bind 的相同实例：


## AngularJS 实例

```html
<div ng-app="" ng-init="person={firstName:'John',lastName:'Doe'}">

<p>姓为 <span ng-bind="person.lastName"></span></p>

</div>
```


## AngularJS 数组

AngularJS 数组就像 JavaScript 数组：


## AngularJS 实例

```html
<div ng-app="" ng-init="points=[1,15,19,2,40]">

<p>第三个值为 {{ points[2] }}</p>

</div>
```

使用 ng-bind 的相同实例：


## AngularJS 实例

```html
<div ng-app="" ng-init="points=[1,15,19,2,40]">

<p>第三个值为 <span ng-bind="points[2]"></span></p>

</div>
```


## AngularJS 表达式 与 JavaScript 表达式

类似于 JavaScript 表达式，AngularJS 表达式可以包含字母，操作符，变量。

与 JavaScript 表达式不同，AngularJS 表达式可以写在 HTML 中。

与 JavaScript 表达式不同，AngularJS 表达式不支持条件判断，循环及异常。

与 JavaScript 表达式不同，AngularJS 表达式支持过滤器。


## 复习重点

- 能说明 `AngularJS 表达式` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
