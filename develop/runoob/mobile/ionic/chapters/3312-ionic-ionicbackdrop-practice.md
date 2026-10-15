# Ionic：ionic 背景层

- 来源：[ionic 背景层](https://www.runoob.com/ionic/ionic-ionicbackdrop.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3312

## 本章内容

我们经常需要在 UI 上，例如在弹出框、加载框、其他弹出层中显示或隐藏背景层。

在组件中可以使用$ionicBackdrop.retain()来显示背景层，使用$ionicBackdrop.release()隐藏背景层。

每次调用retain后，背景会一直显示，直到调用release消除背景层。


## 实例


### HTML 代码

```html
<body ng-app="starter" ng-controller="actionsheetCtl" >
    <ion-pane>
        <ion-content >
            <h2 ng-click="action()">$ionicBackdrop</h2>
        </ion-content>
    </ion-pane>
</body>
```


### JavaScript 代码

```text
angular.module('starter', ['ionic'])

.run(function($ionicPlatform) {
  $ionicPlatform.ready(function() {
    // Hide the accessory bar by default (remove this to show the accessory bar above the keyboard
    // for form inputs)
    if(window.cordova && window.cordova.plugins.Keyboard) {
      cordova.plugins.Keyboard.hideKeyboardAccessoryBar(true);
    }
    if(window.StatusBar) {
      StatusBar.styleDefault();
    }
  });
})

.controller( 'actionsheetCtl',['$scope','$timeout' ,'$ionicBackdrop',function($scope,$timeout,$ionicBackdrop){

    $scope.action = function() {
       $ionicBackdrop.retain();
       $timeout(function() {    //默认让它1秒后消失
         $ionicBackdrop.release();
       }, 1000);
    };
}])
```

尝试一下 »

显示效果如下图所示：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic 背景层` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
