# AngularJS：AngularJS API

- 来源：[AngularJS API](https://www.runoob.com/angularjs/angularjs-api.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：练习笔记
- 章节序号：2295

## 本章内容

API 意为 Application Programming Interface（应用程序编程接口）。


## AngularJS 全局 API

AngularJS 全局 API 用于执行常见任务的 JavaScript 函数集合，如：

- 比较对象
- 迭代对象
- 转换对象

全局 API 函数使用 angular 对象进行访问。

以下列出了一些通用的 API 函数：

注意：自 AngularJS 1.7 之后移除 angular.lowercase 和 angular.uppercase 方法, 改为 angular.$$lowercase 和 angular.$$uppercase


### angular.lowercase()


## 实例

```html
<div ng-app="myApp" ng-controller="myCtrl">
<p>{{ x1 }}</p>
<p>{{ x2 }}</p>
</div>

<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.x1 = "RUNOOB";
    $scope.x2 = angular.$$lowercase($scope.x1);
});
</script>
```


### angular.uppercase()


## 实例

```html
<div ng-app="myApp" ng-controller="myCtrl">
<p>{{ x1 }}</p>
<p>{{ x2 }}</p>
</div>
​
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.x1 = "runoob";
    $scope.x2 = angular.$$uppercase($scope.x1);
});
</script>
​
```


### angular.isString()


## 实例


### angular.isNumber()


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AngularJS API` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
