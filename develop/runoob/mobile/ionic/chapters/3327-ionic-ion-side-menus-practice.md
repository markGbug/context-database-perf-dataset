# Ionic：ionic 侧栏菜单

- 来源：[ionic 侧栏菜单](https://www.runoob.com/ionic/ionic-ion-side-menus.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3327

## 本章内容

一个容器元素包含侧边菜单和主要内容。通过把主要内容区域从一边拖动到另一边，来让左侧或右侧的侧栏菜单进行切换。

效果图如下所示：


### 用法

要使用侧栏菜单，添加一个父元素<ion-side-menus>，一个中间内容 <ion-side-menu-content>，和一个或更多 <ion-side-menu> 指令。

```html
<ion-side-menus>
  <!-- 中间内容 -->
  <ion-side-menu-content ng-controller="ContentController">
  </ion-side-menu-content>

  <!-- 左侧菜单 -->
  <ion-side-menu side="left">
  </ion-side-menu>

  <!-- 右侧菜单 -->
  <ion-side-menu side="right">
  </ion-side-menu>
</ion-side-menus>
```

```javascript
function ContentController($scope, $ionicSideMenuDelegate) {
  $scope.toggleLeft = function() {
    $ionicSideMenuDelegate.toggleLeft();
  };
}
```

尝试一下 »


### API

在返回按钮显示时，确认是否启用侧边栏菜单。


## ion-side-menu-content

一个可见主体内容的容器，同级的一个或多个ionSideMenu 指令。


### 用法

```html
<ion-side-menu-content
  drag-content="true">
</ion-side-menu-content>
```


### API

内容是否可被拖动。默认为true。


## ion-side-menu

一个侧栏菜单的容器，同级的一个ion-side-menu-content 指令。


### 用法

```html
<ion-side-menu
  side="left"
  width="myWidthValue + 20"
  is-enabled="shouldLeftSideMenuBeEnabled()">
</ion-side-menu>
```


### API

侧栏菜单当前在哪一边。可选的值有: 'left' 或 'right'。

该侧栏菜单是否可用。

侧栏菜单应该有多少像素的宽度。默认为275。


## menu-toggle

在一个指定的侧栏中切换菜单。


### 用法

下面是一个在导航栏内链接的例子。点击此链接会自动打开指定的侧栏菜单。

```html
<ion-view>
  <ion-nav-buttons side="left">
   <button menu-toggle="left" class="button button-icon icon ion-navicon"></button>
  </ion-nav-buttons>
 ...
</ion-view>
```


## menu-close

关闭当前打开的侧栏菜单。


### 用法

下面是一个在导航栏内链接的例子。点击此链接会自动打开指定的侧栏菜单。

```html
<a menu-close href="#/home" class="item">首页</a>
```


## $ionicSideMenuDelegate

该方法直接触发$ionicSideMenuDelegate服务，来控制所有侧栏菜单。用$getByHandle方法控制特定情况下的ionSideMenus。


### 用法

```html
<body ng-controller="MainCtrl">
  <ion-side-menus>
    <ion-side-menu-content>
      内容!
      <button ng-click="toggleLeftSideMenu()">
        切换左侧侧栏菜单
      </button>
    </ion-side-menu-content>
    <ion-side-menu side="left">
      左侧菜单!
    <ion-side-menu>
  </ion-side-menus>
</body>
```

```javascript
function MainCtrl($scope, $ionicSideMenuDelegate) {
  $scope.toggleLeftSideMenu = function() {
    $ionicSideMenuDelegate.toggleLeft();
  };
}
```


### 方法

```text
toggleLeft([isOpen])
```

切换左侧侧栏菜单（如果存在）。

是否打开或关闭菜单。默认：切换菜单。

```text
toggleRight([isOpen])
```

切换右侧侧栏菜单（如果存在）。

是否打开或关闭菜单。默认：切换菜单。

```text
getOpenRatio()
```

获取打开菜单内容超出菜单宽度的比例。比如，一个宽度为100px的菜单被宽度为50px以50%的比例打开，将会返回一个比例值为0.5。

返回值: 浮点 0 表示没被打开，如果左侧菜单处于已打开或正在打开为0 到 1，如果右侧菜单处于已打开或正在打开为0 到-1。

```text
isOpen()
```

返回值: 布尔值，判断左侧或右侧菜单是否已经打开。

```text
isOpenLeft()
```

返回值: 布尔值左侧菜单是否已经打开。

```text
isOpenRight()
```

返回值: 布尔值右侧菜单是否已经打开。

```text
canDragContent([canDrag])
```

设置是否可以拖动内容打开侧栏菜单。

返回值: 布尔值，是否可以拖动内容打开侧栏菜单。

```text
$getByHandle(handle)
```

例如:

```text
$ionicSideMenuDelegate.$getByHandle('my-handle').toggleLeft();
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic 侧栏菜单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
