# Ionic：ionic 上拉菜单(ActionSheet)

- 来源：[ionic 上拉菜单](https://www.runoob.com/ionic/ionic-actionsheet.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：学习笔记
- 章节序号：3311

## 本章内容

上拉菜单(ActionSheet)通过往上弹出的框，来让用户选择选项。

非常危险的选项会以高亮的红色来让人第一时间识别。你可以通过点击取消按钮或者点击空白的地方来让它消失。


## 实例


### HTML 代码

```html
<body ng-app="starter" ng-controller="actionsheetCtl" >

    <ion-pane>
        <ion-content >
            <h2 ng-click="show()">Action Sheet</h2>
        </ion-content>
    </ion-pane>
</body>
```


### JavaScript 代码

在代码中触发上拉菜单，需要在你的 angular 控制器中使用 $ionicActionSheet 服务：

```html
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

.controller( 'actionsheetCtl',['$scope','$ionicActionSheet','$timeout' ,function($scope,$ionicActionSheet,$timeout){
    $scope.show = function() {

        var hideSheet = $ionicActionSheet.show({
            buttons: [
              { text: '<b>Share</b> This' },
              { text: 'Move' }
            ],
            destructiveText: 'Delete',
            titleText: 'Modify your album',
            cancelText: 'Cancel',
            cancel: function() {
                 // add cancel code..
               },
            buttonClicked: function(index) {
              return true;
            }
        });

        $timeout(function() {
            hideSheet();
        }, 2000);

    };
}])
```

尝试一下 »

运行效果如下图：


## 复习重点

- 能说明 `ionic 上拉菜单` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
