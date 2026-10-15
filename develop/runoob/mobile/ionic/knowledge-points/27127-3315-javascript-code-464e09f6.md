# 知识点 27127：Ionic：ionic 单选框操作 - JavaScript 代码

- 来源：[ionic 单选框操作](https://www.runoob.com/ionic/ionic-ion-radio.html)
- 来源章节：[3315-ionic-ion-radio-practice.md](../chapters/3315-ionic-ion-radio-practice.md)
- 分类：移动开发
- 技术：Ionic
- 所在小节：JavaScript 代码
- 知识类型：代码
- 原章节序号：3315

## 原文片段

```text
angular.module('ionicApp', ['ionic'])

.controller('MainCtrl', function($scope) {

  $scope.clientSideList = [
    { text: "Backbone", value: "bb" },
    { text: "Angular", value: "ng" },
    { text: "Ember", value: "em" },
    { text: "Knockout", value: "ko" }
  ];

  $scope.serverSideList = [
    { text: "Go", value: "go" },
    { text: "Python", value: "py" },
    { text: "Ruby", value: "rb" },
    { text: "Java", value: "jv" }
  ];

  $scope.data = {
    clientSide: 'ng'
  };

  $scope.serverSideChange = function(item) {
    console.log("Selected Serverside, text:", item.text, "value:", item.value);
  };

});
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `JavaScript 代码` 这一小节和 `ionic 单选框操作` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
