# Ionic：ionic 加载动作

- 来源：[ionic 加载动作](https://www.runoob.com/ionic/ionic-ionicloading.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：学习笔记
- 章节序号：3320

## 本章内容

$ionicLoading 是 ionic 默认的一个加载交互效果。里面的内容也是可以在模板里面修改。


### 用法

```text
angular.module('LoadingApp', ['ionic'])
.controller('LoadingCtrl', function($scope, $ionicLoading) {
  $scope.show = function() {
    $ionicLoading.show({
      template: 'Loading...'
    });
  };
  $scope.hide = function(){
    $ionicLoading.hide();
  };
});
```


### 方法

显示一个加载效果。

```text
show(opts)
```

loading指示器的选项。可用属性：

- {string=} template 指示器的html内容。
- {string=} templateUrl 一个加载html模板的url作为指示器的内容。
- {boolean=} noBackdrop 是否隐藏背景。默认情况下它会显示。
- {number=} delay 指示器延迟多少毫秒显示。默认为不延迟。
- {number=} duration 等待多少毫秒后自动隐藏指示器。默认情况下，指示器会一直显示，直到触发.hide()。

隐藏一个加载效果。

```text
hide()
```


### API

该句柄定义带有$ionicListDelegate的列表。

列表项的删除按钮当前是显示还是隐藏。

列表项的排序按钮当前是显示还是隐藏。

列表项是否被允许滑动显示选项按钮。默认：true。


## 实例


### HTML 代码：

```html
<html ng-app="ionicApp">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no, width=device-width">

    <title>Ionic Modal</title>

     <link href="http://www.runoob.com/static/ionic/css/ionic.min.css" rel="stylesheet">
    <script src="http://www.runoob.com/static/ionic/js/ionic.bundle.min.js"></script>
  </head>
  <body ng-controller="AppCtrl">

      <ion-view title="Home">
        <ion-header-bar>
          <h1 class="title">The Stooges</h1>
        </ion-header-bar>
        <ion-content has-header="true">
          <ion-list>
            <ion-item ng-repeat="stooge in stooges" href="#">{{stooge.name}}</ion-item>
          </ion-list>
        </ion-content>
      </ion-view>

  </body>
</html>
```


### JavaScript 代码

```javascript
angular.module('ionicApp', ['ionic'])
.controller('AppCtrl', function($scope, $timeout, $ionicLoading) {

  // Setup the loader
  $ionicLoading.show({
    content: 'Loading',
    animation: 'fade-in',
    showBackdrop: true,
    maxWidth: 200,
    showDelay: 0
  });

  // Set a timeout to clear loader, however you would actually call the $ionicLoading.hide(); method whenever everything is ready or loaded.
  $timeout(function () {
    $ionicLoading.hide();
    $scope.stooges = [{name: 'Moe'}, {name: 'Larry'}, {name: 'Curly'}];
  }, 2000);

});
```

尝试一下 »


## $ionicLoadingConfig

设置加载的默认选项:


### 用法:

```javascript
var app = angular.module('myApp', ['ionic'])
app.constant('$ionicLoadingConfig', {
  template: '默认加载模板……'
});
app.controller('AppCtrl', function($scope, $ionicLoading) {
  $scope.showLoading = function() {
    $ionicLoading.show(); //配置选项在 $ionicLoadingConfig 设置
  };
});
```


## 复习重点

- 能说明 `ionic 加载动作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
