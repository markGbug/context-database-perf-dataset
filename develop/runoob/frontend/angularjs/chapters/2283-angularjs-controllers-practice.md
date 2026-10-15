# AngularJS：AngularJS 控制器

- 来源：[AngularJS 控制器](https://www.runoob.com/angularjs/angularjs-controllers.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：练习笔记
- 章节序号：2283

## 本章内容

AngularJS 控制器 控制 AngularJS 应用程序的数据。

AngularJS 控制器是常规的 JavaScript 对象。


## AngularJS 控制器

AngularJS 应用程序被控制器控制。

ng-controller 指令定义了应用程序控制器。

控制器是 JavaScript 对象，由标准的 JavaScript 对象的构造函数 创建。


## AngularJS 实例

应用解析：

AngularJS 应用程序由 ng-app 定义。应用程序在 <div> 内运行。

ng-controller="myCtrl" 属性是一个 AngularJS 指令。用于定义一个控制器。

myCtrl 函数是一个 JavaScript 函数。

AngularJS 使用$scope 对象来调用控制器。

在 AngularJS 中， $scope 是一个应用对象(属于应用变量和函数)。

控制器的 $scope （相当于作用域、控制范围）用来保存AngularJS Model(模型)的对象。

控制器在作用域中创建了两个属性 (firstName 和 lastName)。

ng-model 指令绑定输入域到控制器的属性（firstName 和 lastName）。


## 控制器方法

上面的实例演示了一个带有 lastName 和 firstName 这两个属性的控制器对象。

控制器也可以有方法（变量和函数）：


## AngularJS 实例


## 外部文件中的控制器

在大型的应用程序中，通常是把控制器存储在外部文件中。

只需要把 <script> 标签中的代码复制到名为 personController.js 的外部文件中即可：


## AngularJS 实例


## 其他实例

以下实例创建一个新的控制器文件:

```text
angular.module('myApp', []).controller('namesCtrl', function($scope) {
    $scope.names = [
        {name:'Jani',country:'Norway'},
        {name:'Hege',country:'Sweden'},
        {name:'Kai',country:'Denmark'}
    ];
});
```

保存文件为 namesController.js:

然后，在应用中使用控制器文件:


## AngularJS 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AngularJS 控制器` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
