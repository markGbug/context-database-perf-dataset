# Ionic：ionic 滑动框

- 来源：[ionic 滑动框](https://www.runoob.com/ionic/ionic-ion-slide-box.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：学习笔记
- 章节序号：3328

## 本章内容

## ion-slide-box

滑动框是一个包含多页容器的组件，每页滑动或拖动切换：

效果图如下：


### 用法

```html
<ion-slide-box on-slide-changed="slideHasChanged($index)">
  <ion-slide>
    <div class="box blue"><h1>BLUE</h1></div>
  </ion-slide>
  <ion-slide>
    <div class="box yellow"><h1>YELLOW</h1></div>
  </ion-slide>
  <ion-slide>
    <div class="box pink"><h1>PINK</h1></div>
  </ion-slide>
</ion-slide-box>
```


### API

该句柄用$ionicSlideBoxDelegate来标识这个滑动框。

滑动框是否开启循环滚动。

设置滑动框是否循环播放，如果 does-continue 为 true，默认也为 true。

等待多少毫秒开始滑动（如果继续则为true）。默认为4000。

滑动框的页面是否显示。

当点击页面时，触发该表达式（如果shou-pager为true）。传递一个'索引'变量。

当滑动时，触发该表达式。传递一个'索引'变量。

将模型绑定到当前滑动框。


## 实例


### HTML 代码

```html
<ion-slide-box active-slide="myActiveSlide">
    <ion-slide>
      <div class="box blue"><h1>BLUE</h1></div>
    </ion-slide>
    <ion-slide>
      <div class="box yellow"><h1>YELLOW</h1></div>
    </ion-slide>
    <ion-slide>
      <div class="box pink"><h1>PINK</h1></div>
    </ion-slide>
</ion-slide-box>
```


### CSS 代码

```text
.slider {
  height: 100%;
}
.slider-slide {
  color: #000;
  background-color: #fff; text-align: center;
  font-family: "HelveticaNeue-Light", "Helvetica Neue Light", "Helvetica Neue", Helvetica, Arial, "Lucida Grande", sans-serif; font-weight: 300; }
.blue {
  background-color: blue;
}

.yellow {
  background-color: yellow;
}

.pink {
  background-color: pink;
}
.box{
  height:100%;
}
.box h1{
  position:relative; top:50%; transform:translateY(-50%);
}
```


### JavaScript 代码

```text
angular.module('ionicApp', ['ionic'])

.controller('SlideController', function($scope) {

  $scope.myActiveSlide = 1;

})
```

尝试一下 »


## 复习重点

- 能说明 `ionic 滑动框` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
