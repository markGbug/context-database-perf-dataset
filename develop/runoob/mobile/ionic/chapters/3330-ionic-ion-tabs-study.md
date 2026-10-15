# Ionic：ionic 选项卡栏操作

- 来源：[ionic 选项卡栏操作](https://www.runoob.com/ionic/ionic-ion-tabs.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：学习笔记
- 章节序号：3330

## 本章内容

## ion-tabs

ion-tabs 是有一组页面选项卡组成的选项卡栏。可以通过点击选项来切换页面。

对于 iOS，它会出现在屏幕的底部，Android会出现在屏幕的顶部(导航栏下面)。


### 用法


## 实例

```html
<ion-tabs class="tabs-positive tabs-icon-only">

  <ion-tab title="首页" icon-on="ion-ios-filing" icon-off="ion-ios-filing-outline">
    <!-- 标签 1 内容 -->
  </ion-tab>

  <ion-tab title="关于" icon-on="ion-ios-clock" icon-off="ion-ios-clock-outline">
    <!-- 标签 2 内容 -->
  </ion-tab>

  <ion-tab title="设置" icon-on="ion-ios-gear" icon-off="ion-ios-gear-outline">
    <!-- 标签 3 内容 -->
  </ion-tab>
</ion-tabs>
```

效果如下所示：


### API

该句柄用$ionicTabsDelegate来标识这些选项卡。


## ion-tab

隶属于ionTabs

包含一个选项卡内容。该内容仅存在于被选中的给定选项卡中。

每个ionTab都有自己的浏览历史。


### 用法

```html
<ion-tab
  title="Tab!"
  icon="my-icon"
  href="#/tab/tab-link"
  on-select="onTabSelected()"
  on-deselect="onTabDeselected()">
</ion-tab>
```


### API

选项卡的标题。

当触碰的时候，该选项卡将会跳转的的链接。

选项卡的图标。如果给定值，它将成为ion-on和ion-off的默认值。

被选中标签的图标。

没被选中标签的图标。

选项卡上的徽章（通常是一个数字）。

选项卡上微章的样式（例，tabs-positive ）。

选项卡被选中时触发。

选项卡取消选中时触发。

通常，点击时选项卡会被选中。如果设置了 ng-Click，它将不会被选中。 你可以用$ionicTabsDelegate.select()来指定切换标签。


## $ionicTabsDelegate

授权控制ionTabs指令。

该方法直接调用$ionicTabsDelegate服务，控制所有ionTabs指令。用$getByHandle方法控制具体的ionTabs实例。


### 用法

```html
<body ng-controller="MyCtrl">
  <ion-tabs>

    <ion-tab title="Tab 1">
      你好，标签1！
      <button ng-click="selectTabWithIndex(1)">选择标签2</button>
    </ion-tab>
    <ion-tab title="Tab 2">你好标签2！</ion-tab>

  </ion-tabs>
</body>
```

```javascript
function MyCtrl($scope, $ionicTabsDelegate) {
  $scope.selectTabWithIndex = function(index) {
    $ionicTabsDelegate.select(index);
  }
}
```


### 方法

```text
select(index, [shouldChangeHistory])
```

选择标签来匹配给定的索引。

选择标签的索引。

此选项是否应该加载这个标签的浏览历史（如果存在），并使用，或仅加载默认页面。默认为false。提示：如果一个ion-nav-view在选项卡里，你可能需要设置它为true。

```text
selectedIndex()
```

返回值: 数值, 被选中标签的索引，如 -1。

```text
$getByHandle(handle)
```

例如:

```text
$ionicTabsDelegate.$getByHandle('my-handle').select(0);
```


## 复习重点

- 能说明 `ionic 选项卡栏操作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
