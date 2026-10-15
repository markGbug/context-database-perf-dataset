# Ionic：ionic 对话框

- 来源：[ionic 对话框](https://www.runoob.com/ionic/ionic-ionicpopup.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3325

## 本章内容

## $ionicPopup

ionic 对话框服务允许程序创建、显示弹出窗口。

$ionicPopup 提供了3个方法：alert(), prompt(),以及 confirm() 。


## 实例


### HTML 代码

```html
<body class="padding" ng-controller="PopupCtrl">
    <button class="button button-dark" ng-click="showPopup()">
      弹窗显示
    </button>
    <button class="button button-primary" ng-click="showConfirm()">
      确认对话框
    </button>
    <button class="button button-positive" ng-click="showAlert()">
      警告框
    </button>

    <script id="popup-template.html" type="text/ng-template">
      <input ng-model="data.wifi" type="text" placeholder="Password">
    </script>
</body>
```


### JavaScript 代码

```html
angular.module('mySuperApp', ['ionic'])
.controller('PopupCtrl',function($scope, $ionicPopup, $timeout) {

 // Triggered on a button click, or some other target
 $scope.showPopup = function() {
   $scope.data = {}

   // 自定义弹窗
   var myPopup = $ionicPopup.show({
     template: '<input type="password" ng-model="data.wifi">',
     title: 'Enter Wi-Fi Password',
     subTitle: 'Please use normal things',
     scope: $scope,
     buttons: [
       { text: 'Cancel' },
       {
         text: '<b>Save</b>',
         type: 'button-positive',
         onTap: function(e) {
           if (!$scope.data.wifi) {
             // 不允许用户关闭，除非输入 wifi 密码
             e.preventDefault();
           } else {
             return $scope.data.wifi;
           }
         }
       },
     ]
   });
   myPopup.then(function(res) {
     console.log('Tapped!', res);
   });
   $timeout(function() {
      myPopup.close(); // 3秒后关闭弹窗
   }, 3000);
  };
   //  confirm 对话框
   $scope.showConfirm = function() {
     var confirmPopup = $ionicPopup.confirm({
       title: 'Consume Ice Cream',
       template: 'Are you sure you want to eat this ice cream?'
     });
     confirmPopup.then(function(res) {
       if(res) {
         console.log('You are sure');
       } else {
         console.log('You are not sure');
       }
     });
   };

   //  alert（警告） 对话框
   $scope.showAlert = function() {
     var alertPopup = $ionicPopup.alert({
       title: 'Don\'t eat that!',
       template: 'It might taste good'
     });
     alertPopup.then(function(res) {
       console.log('Thank you for not eating my delicious ice cream cone');
     });
   };
});
```

尝试一下 »


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic 对话框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
