# Ionic：ionic 模态窗口

- 来源：[ionic 模态窗口](https://www.runoob.com/ionic/ionic-ion-modal.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3321

## 本章内容

## $ionicModal

$ionicModal 可以遮住用户主界面的内容框。

你可以在你的 index 文件或者是其他文件内嵌入以下代码(里面的代码可以根据你自己的业务场景相应的改变)。

```html
<script id="my-modal.html" type="text/ng-template">
  <ion-modal-view>
    <ion-header-bar>
      <h1 class="title">My Modal title</h1>
    </ion-header-bar>
    <ion-content>
      Hello!
    </ion-content>
  </ion-modal-view>
</script>
```

然后你就可以在你的 Controller 里面的注入 $ionicModal 。然后调用你刚刚写入的模板，进行初始化操作。就像下面的代码：

```text
angular.module('testApp', ['ionic'])
.controller('MyController', function($scope, $ionicModal) {
  $ionicModal.fromTemplateUrl('my-modal.html', {
    scope: $scope,
    animation: 'slide-in-up'
  }).then(function(modal) {
    $scope.modal = modal;
  });
  $scope.openModal = function() {
    $scope.modal.show();
  };
  $scope.closeModal = function() {
    $scope.modal.hide();
  };
  //Cleanup the modal when we're done with it!
  $scope.$on('$destroy', function() {
    $scope.modal.remove();
  });
  // Execute action on hide modal
  $scope.$on('modal.hidden', function() {
    // Execute action
  });
  // Execute action on remove modal
  $scope.$on('modal.removed', function() {
    // Execute action
  });
});
```


### 方法

```text
fromTemplate(templateString, options)
```

模板的字符串作为模态窗口的内容。

options 会传递到 ionicModal#initialize方法中。

返回: 对象, 一个ionicModal控制器的实例。

```text
fromTemplateUrl(templateUrl, options)
```

载入模板的url。

通过ionicModal#initialize方法传递对象。

返回： promise对象。Promises对象是CommonJS工作组提出的一种规范，目的是为异步编程提供统一接口。


## ionicModal

由$ionicModal服务实例化。

提示：当你完成每个模块清除时，确保调用remove()方法，以避免内存泄漏。

注意：一个模块从它的初始范围广播出 'modal.shown' 和 'modal.hidden' ，把自身作为一个参数来传递。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic 模态窗口` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
