# Ionic：ionic 浮动框

- 来源：[ionic 浮动框](https://www.runoob.com/ionic/ionic-ionicpopover.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3324

## 本章内容

## $ionicPopover

$ionicPopover 是一个可以浮在app内容上的一个视图框。

可以实现以下功能点：

- 在当前页面显示更多信息。
- 选择一些工具或配置。
- 在页面提供一个操作列表。


### 方法

```text
fromTemplate(templateString, options)
或
fromTemplateUrl(templateUrl, options)
```

参数说明：

templateString: 模板字符串。

templateUrl: 载入的模板 URL。

options: 初始化选项。


## 实例


## HTML 代码部分

```html
<p>
<button ng-click="openPopover($event)">打开浮动框</button>
</p>
<script id="my-popover.html" type="text/ng-template">
<ion-popover-view>
  <ion-header-bar>
    <h1 class="title">我的浮动框标题</h1>
  </ion-header-bar>
  <ion-content>
    Hello!
  </ion-content>
</ion-popover-view>
</script>
```


## fromTemplateUrl 方法

```text
angular.module('ionicApp', ['ionic'])
.controller( 'AppCtrl',['$scope','$ionicPopover','$timeout',function($scope,$ionicPopover,$timeout){

  $scope.popover = $ionicPopover.fromTemplateUrl('my-popover.html', {
    scope: $scope
  });

  // .fromTemplateUrl() 方法
  $ionicPopover.fromTemplateUrl('my-popover.html', {
    scope: $scope
  }).then(function(popover) {
    $scope.popover = popover;
  });


  $scope.openPopover = function($event) {
    $scope.popover.show($event);
  };
  $scope.closePopover = function() {
    $scope.popover.hide();
  };
  // 清除浮动框
  $scope.$on('$destroy', function() {
    $scope.popover.remove();
  });
  // 在隐藏浮动框后执行
  $scope.$on('popover.hidden', function() {
    // 执行代码
  });
  // 移除浮动框后执行
  $scope.$on('popover.removed', function() {
    // 执行代码
  });

}])
```

我们也可以把模板当作一个字符串，使用 .fromTemplate() 方法来实现弹框:


## fromTemplate 方法

```html
angular.module('ionicApp', ['ionic'])
.controller( 'AppCtrl',['$scope','$ionicPopover','$timeout',function($scope,$ionicPopover,$timeout){

  $scope.popover = $ionicPopover.fromTemplateUrl('my-popover.html', {
    scope: $scope
  });
  // .fromTemplate() 方法
  var template = '<ion-popover-view><ion-header-bar> <h1 class="title">我的浮动框标题</h1> </ion-header-bar> <ion-content> Hello! </ion-content></ion-popover-view>';
      $scope.popover = $ionicPopover.fromTemplate(template, {
    scope: $scope
  });



  $scope.openPopover = function($event) {
    $scope.popover.show($event);
  };
  $scope.closePopover = function() {
    $scope.popover.hide();
  };
  // 清除浮动框
  $scope.$on('$destroy', function() {
    $scope.popover.remove();
  });
  // 在隐藏浮动框后执行
  $scope.$on('popover.hidden', function() {
    // 执行代码
  });
  // 移除浮动框后执行
  $scope.$on('popover.removed', function() {
    // 执行代码
  });

}])
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic 浮动框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
