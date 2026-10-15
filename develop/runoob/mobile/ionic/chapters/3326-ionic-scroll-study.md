# Ionic：ionic 滚动条

- 来源：[ionic 滚动条](https://www.runoob.com/ionic/ionic-scroll.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：学习笔记
- 章节序号：3326

## 本章内容

## ion-scroll

ion-scroll 用于创建一个可滚动的容器。


### 用法

```html
<ion-scroll
    [delegate-handle=""]
    [direction=""]
    [paging=""]
    [on-refresh=""]
    [on-scroll=""]
    [scrollbar-x=""]
    [scrollbar-y=""]
    [zooming=""]
    [min-zoom=""]
    [max-zoom=""]>
    ...
</ion-scroll>
```


### API

该句柄利用$ionicScrollDelegate指定滚动视图。

滚动的方向。 'x' 或 'y'。 默认 'y'。

分页是否滚动。

调用下拉刷新， 由ionRefresher触发。

当用户滚动时触发。

是否显示水平滚动条。默认为false。

是否显示垂直滚动条。默认为true。

是否支持双指缩放。

允许的最小缩放量（默认为0.5）

允许的最大缩放量（默认为3）


### 实例


### HTML 代码

```html
<ion-scroll zooming="true" direction="xy" style="width: 500px; height: 500px">
    <div style="width: 5000px; height: 5000px; background: url('http://www.runoob.com/try/demo_source/Europe_geological_map-en.jpg') repeat"></div>
</ion-scroll>
```


### CSS 代码

```text
body {
  cursor: url('http://www.runoob.com/try/demo_source/finger.png'), auto;
}
```


### JavaScript 代码

```text
angular.module('ionicApp', ['ionic']);
```

尝试一下 »


## ion-infinite-scroll

当用户到达页脚或页脚附近时，ionInfiniteScroll指令允许你调用一个函数 。

当用户滚动的距离超出底部的内容时，就会触发你指定的on-infinite。


### 用法

```html
<ion-content ng-controller="MyController">
  <ion-infinite-scroll
    on-infinite="loadMore()"
    distance="1%">
  </ion-infinite-scroll>
</ion-content>
```

```javascript
function MyController($scope, $http) {
  $scope.items = [];
  $scope.loadMore = function() {
    $http.get('/more-items').success(function(items) {
      useItems(items);
      $scope.$broadcast('scroll.infiniteScrollComplete');
    });
  };

  $scope.$on('stateChangeSuccess', function() {
    $scope.loadMore();
  });
}
```

当没有更多数据加载时，就可以用一个简单的方法阻止无限滚动，那就是angular的ng-if 指令:

```html
<ion-infinite-scroll
  ng-if="moreDataCanBeLoaded()"
  icon="ion-loading-c"
  on-infinite="loadMoreData()">
</ion-infinite-scroll>
```


### API

当滚动到底部时触发的事件。

从底部滚动到触发on-infinite表达式的距离。默认: 1%。

当加载时显示的图标。默认: 'ion-loading-d'。


## $ionicScrollDelegate

授权控制滚动视图（通过ion-content 和 ion-scroll指令创建）。

该方法直接被$ionicScrollDelegate服务触发，来控制所有滚动视图。用 $getByHandle方法控制特定的滚动视图。


### 用法

```html
<body ng-controller="MainCtrl">
  <ion-content>
    <button ng-click="scrollTop()">滚动到顶部!</button>
  </ion-content>
</body>
```

```javascript
function MainCtrl($scope, $ionicScrollDelegate) {
  $scope.scrollTop = function() {
    $ionicScrollDelegate.scrollTop();
  };
}
```


### 方法

```text
resize()
```

告诉滚动视图重新计算它的容器大小。

```text
scrollTop([shouldAnimate])
```

是否应用滚动动画。

```text
scrollBottom([shouldAnimate])
```

是否应用滚动动画。


## 复习重点

- 能说明 `ionic 滚动条` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
