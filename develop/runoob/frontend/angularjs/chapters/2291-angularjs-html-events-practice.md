# AngularJS：AngularJS 事件

- 来源：[AngularJS 事件](https://www.runoob.com/angularjs/angularjs-html-events.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：练习笔记
- 章节序号：2291

## 本章内容

AngularJS 有自己的 HTML 事件指令。


## ng-click 指令

ng-click 指令定义了 AngularJS 点击事件。


## AngularJS 实例


## 隐藏 HTML 元素

ng-hide 指令用于设置应用部分是否可见。

ng-hide="true" 设置 HTML 元素不可见。

ng-hide="false" 设置 HTML 元素可见。


## AngularJS 实例

应用解析:

第一部分 personController与控制器章节类似。

应用有一个默认属性: $scope.myVar = false;

ng-hide 指令设置 <p>元素及两个输入域是否可见， 根据 myVar 的值 (true 或 false) 来设置是否可见。

toggle() 函数用于切换 myVar 变量的值（true 和 false）。

ng-hide="true" 让元素 不可见。


## 显示 HTML 元素

ng-show 指令可用于设置应用中的一部分是否可见 。

ng-show="false" 可以设置 HTML 元素 不可见。

ng-show="true" 可以以设置 HTML 元素可见。

以下实例使用了 ng-show 指令:


## AngularJS 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AngularJS 事件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
