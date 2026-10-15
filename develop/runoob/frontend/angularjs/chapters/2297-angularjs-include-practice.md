# AngularJS：AngularJS 包含

- 来源：[AngularJS 包含](https://www.runoob.com/angularjs/angularjs-include.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：练习笔记
- 章节序号：2297

## 本章内容

在 AngularJS 中，你可以在 HTML 中包含 HTML 文件。


## 在 HTML 中包含 HTML 文件

在 HTML 中，目前还不支持包含 HTML 文件的功能。


## 服务端包含

大多服务端脚本都支持包含文件功能 (SSI： Server Side Includes)。

使用 SSI, 你可在 HTML 中包含 HTML 文件，并发送到客户端浏览器。


## PHP 实例


## 客户端包含

通过 JavaScript 有很多种方式可以在 HTML 中包含 HTML 文件。

通常我们使用 http 请求 (AJAX) 从服务端获取数据，返回的数据我们可以通过 使用 innerHTML 写入到 HTML 元素中。


## AngularJS 包含

使用 AngularJS, 你可以使用 ng-include 指令来包含 HTML 内容:


## 实例

```html
<body ng-app="">

<div ng-include="'runoob.htm'"></div>

</body>
```

步骤如下：


## runoob.htm 文件代码：

```html
<h1>菜鸟教程</h1>
<p>这是一个被包含的 HTML 页面，使用 ng-include 指令来实现！</p>
```


## 包含 AngularJS 代码

ng-include 指令除了可以包含 HTML 文件外，还可以包含 AngularJS 代码:


## sites.htm 文件代码：

```html
<table>
<tr ng-repeat="x in names">
<td>{{ x.Name }}</td>
<td>{{ x.Url }}</td>
</tr>
</table>
```

包含的文件 "sites.php" 中有 AngularJS 代码，它将被正常执行：


## 实例

```html
<div ng-app="myApp" ng-controller="sitesCtrl">
  <div ng-include="'sites.htm'"></div>
</div>

<script>
var app = angular.module('myApp', []);
app.controller('sitesCtrl', function($scope, $http) {
    $http.get("sites.php").then(function (response) {
        $scope.names = response.data.records;
    });
});
</script>
```


## 跨域包含

默认情况下， ng-include 指令不允许包含其他域名的文件。

如果你需要包含其他域名的文件，你需要设置域名访问白名单：


## sites.htm 文件代码：

```html
<body ng-app="myApp">

<div ng-include="'https://c.runoob.com/runoobtest/angular_include.php'"></div>

<script>
var app = angular.module('myApp', [])
app.config(function($sceDelegateProvider) {
    $sceDelegateProvider.resourceUrlWhitelist([
        'https://c.runoob.com/runoobtest/**'
    ]);
});
</script>

</body>
```

此外，你还需要设置服务端允许跨域访问，设置方法可参考：PHP Ajax 跨域问题最佳解决方案。


## angular_include.php 文件代码：

```html
<?php
// 允许所有域名可以访问
header('Access-Control-Allow-Origin:*');

echo '<b style="color:red">我是跨域的内容</b>';
?>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AngularJS 包含` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
