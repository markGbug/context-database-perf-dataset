# Ionic：ionic 列表操作

- 来源：[ionic 列表操作](https://www.runoob.com/ionic/ionic-ion-list.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3319

## 本章内容

列表是一个应用广泛在几乎所有移动app中的界面元素。ionList 和 ionItem 这两个指令还支持多种多样的交互模式，比如移除其中的某一项，拖动重新排序，滑动编辑等等。


### 用法

```html
<ion-list>
  <ion-item ng-repeat="item in items">
    Hello, {{item}}!
  </ion-item>
</ion-list>
```


### 高级用法: 缩略图，删除按钮，重新排序，滑动

```html
<ion-list ng-controller="MyCtrl"
          show-delete="shouldShowDelete"
          show-reorder="shouldShowReorder"
          can-swipe="listCanSwipe">
  <ion-item ng-repeat="item in items"
            class="item-thumbnail-left">

    <img ng-src="{{item.img}}">
    <h2>{{item.title}}</h2>
    <p>{{item.description}}</p>
    <ion-option-button class="button-positive"
                       ng-click="share(item)">
      分享
    </ion-option-button>
    <ion-option-button class="button-info"
                       ng-click="edit(item)">
      编辑
    </ion-option-button>
    <ion-delete-button class="ion-minus-circled"
                       ng-click="items.splice($index, 1)">
    </ion-delete-button>
    <ion-reorder-button class="ion-navicon"
                        on-reorder="reorderItem(item, $fromIndex, $toIndex)">
    </ion-reorder-button>

  </ion-item>
</ion-list>
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
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no">
    <title>Ionic List Directive</title>

    <link href="http://www.runoob.com/static/ionic/css/ionic.min.css" rel="stylesheet">
    <script src="http://www.runoob.com/static/ionic/js/ionic.bundle.min.js"></script>
  </head>

  <body ng-controller="MyCtrl">

    <ion-header-bar class="bar-positive">
      <div class="buttons">
        <button class="button button-icon icon ion-ios-minus-outline"
          ng-click="data.showDelete = !data.showDelete; data.showReorder = false"></button>
      </div>
      <h1 class="title">Ionic Delete/Option Buttons</h1>
      <div class="buttons">
        <button class="button" ng-click="data.showDelete = false; data.showReorder = !data.showReorder">
            Reorder
        </button>
      </div>
    </ion-header-bar>

    <ion-content>

      <!-- The list directive is great, but be sure to also checkout the collection repeat directive when scrolling through large lists -->

      <ion-list show-delete="data.showDelete" show-reorder="data.showReorder">

        <ion-item ng-repeat="item in items"
                  item="item"
                  href="#/item/{{item.id}}" class="item-remove-animate">
          Item {{ item.id }}
          <ion-delete-button class="ion-minus-circled"
                             ng-click="onItemDelete(item)">
          </ion-delete-button>
          <ion-option-button class="button-assertive"
                             ng-click="edit(item)">
            Edit
          </ion-option-button>
          <ion-option-button class="button-calm"
                             ng-click="share(item)">
            Share
          </ion-option-button>
          <ion-reorder-button class="ion-navicon" on-reorder="moveItem(item, $fromIndex, $toIndex)"></ion-reorder-button>
        </ion-item>

      </ion-list>

    </ion-content>

  </body>
</html>
```


### CSS 代码

```text
body {
  cursor: url('http://www.runoob.com/try/demo_source/finger.png'), auto;
}
```


### JavaScript 代码

```text
angular.module('ionicApp', ['ionic'])

.controller('MyCtrl', function($scope) {

  $scope.data = {
    showDelete: false
  };

  $scope.edit = function(item) {
    alert('Edit Item: ' + item.id);
  };
  $scope.share = function(item) {
    alert('Share Item: ' + item.id);
  };

  $scope.moveItem = function(item, fromIndex, toIndex) {
    $scope.items.splice(fromIndex, 1);
    $scope.items.splice(toIndex, 0, item);
  };

  $scope.onItemDelete = function(item) {
    $scope.items.splice($scope.items.indexOf(item), 1);
  };

  $scope.items = [
    { id: 0 },
    { id: 1 },
    { id: 2 },
    { id: 3 },
    { id: 4 },
    { id: 5 },
    { id: 6 },
    { id: 7 },
    { id: 8 },
    { id: 9 },
    { id: 10 },
    { id: 11 },
    { id: 12 },
    { id: 13 },
    { id: 14 },
    { id: 15 },
    { id: 16 },
    { id: 17 },
    { id: 18 },
    { id: 19 },
    { id: 20 },
    { id: 21 },
    { id: 22 },
    { id: 23 },
    { id: 24 },
    { id: 25 },
    { id: 26 },
    { id: 27 },
    { id: 28 },
    { id: 29 },
    { id: 30 },
    { id: 31 },
    { id: 32 },
    { id: 33 },
    { id: 34 },
    { id: 35 },
    { id: 36 },
    { id: 37 },
    { id: 38 },
    { id: 39 },
    { id: 40 },
    { id: 41 },
    { id: 42 },
    { id: 43 },
    { id: 44 },
    { id: 45 },
    { id: 46 },
    { id: 47 },
    { id: 48 },
    { id: 49 },
    { id: 50 }
  ];

});
```

尝试一下 »


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic 列表操作` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
