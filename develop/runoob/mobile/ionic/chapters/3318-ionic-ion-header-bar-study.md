# Ionic：ionic 头部和底部

- 来源：[ionic 头部和底部](https://www.runoob.com/ionic/ionic-ion-header-bar.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：学习笔记
- 章节序号：3318

## 本章内容

## ion-header-bar

这个是固定在屏幕顶部的一个头部标题栏。如果给它加上'bar-subheader' 这个样式，它就是副标题。


### 用法

```html
<ion-header-bar align-title="left" class="bar-positive">
  <div class="buttons">
    <button class="button" ng-click="doSomething()">Left Button</button>
  </div>
  <h1 class="title">Title!</h1>
  <div class="buttons">
    <button class="button">Right Button</button>
  </div>
</ion-header-bar>
<ion-content>
  Some content!
</ion-content>
```


### API

这个是对齐 title 的。如果没有设置，它将会按照手机的默认排版(Ios的默认是居中，Android默认是居左)。它的值可以是 'left','center','right'。

默认情况下，头部标题栏在点击屏幕时内容会滚动到头部，可以将 no-tap-scroll 设置为 true 来禁止该动作。。它的值是布尔值（true/false）。


## ion-footer-bar

知道了 ion-header-bar ，理解ion-footer-bar就轻松多啦！只是 ion-footer-bar 是在屏幕的底部。 用法 <ion-content> Some content! </ion-content> <ion-footer-bar align-title="left" class="bar-assertive"> <div class="buttons"> <button class="button">Left Button</button> </div> <h1 class="title">Title!</h1> <div class="buttons" ng-click="doSomething()"> <button class="button">Right Button</button> </div> </ion-footer-bar> API

这个是对齐 title 的。如果没有设置，它将会按照手机的默认排版(Ios的默认是居中，Android默认是居左)。它的值可以是 'left','center','right'。


## 复习重点

- 能说明 `ionic 头部和底部` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
