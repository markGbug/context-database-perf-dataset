# AngularJS：AngularJS ng-model 指令

- 来源：[AngularJS 模型](https://www.runoob.com/angularjs/angularjs-model.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：练习笔记
- 章节序号：2281

## 本章内容

ng-model 指令用于绑定应用程序数据到 HTML 控制器(input, select, textarea)的值。


## ng-model 指令

ng-model 指令可以将输入域的值与 AngularJS 创建的变量绑定。


## AngularJS 实例


## 双向绑定

双向绑定，在修改输入域的值时， AngularJS 属性的值也将修改：


## AngularJS 实例


## 验证用户输入


## AngularJS 实例

以上实例中，提示信息会在 ng-show 属性返回 true 的情况下显示。


## 应用状态

ng-model 指令可以为应用数据提供状态值(invalid, dirty, touched, error):


## AngularJS 实例

```html
<form ng-app="" name="myForm" ng-init="myText = 'test@runoob.com'">

Email:
<input type="email" name="myAddress" ng-model="myText" required>
<p>编辑邮箱地址，查看状态的改变。</p>
<h1>状态</h1>
<p>Valid: {{myForm.myAddress.$valid}} (如果输入的值是合法的则为 true)。</p>
<p>Dirty: {{myForm.myAddress.$dirty}} (如果值改变则为 true)。</p>
<p>Touched: {{myForm.myAddress.$touched}} (如果通过触屏点击则为 true)。</p>
```


## CSS 类

ng-model 指令基于它们的状态为 HTML 元素提供了 CSS 类：


## AngularJS 实例

ng-model 指令根据表单域的状态添加/移除以下类：

- ng-empty
- ng-not-empty
- ng-touched
- ng-untouched
- ng-valid
- ng-invalid
- ng-dirty
- ng-pending
- ng-pristine


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AngularJS 模型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
