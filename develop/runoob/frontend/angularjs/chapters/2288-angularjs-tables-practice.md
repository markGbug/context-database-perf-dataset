# AngularJS：AngularJS 表格

- 来源：[AngularJS 表格](https://www.runoob.com/angularjs/angularjs-tables.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：练习笔记
- 章节序号：2288

## 本章内容

ng-repeat 指令可以完美的显示表格。


## 在表格中显示数据

使用 angular 显示表格是非常简单的：


## AngularJS 实例

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<script src="https://cdn.bootcss.com/angular.js/1.6.3/angular.min.js"></script>
</head>
<body>

<div ng-app="myApp" ng-controller="customersCtrl">

<table>
  <tr ng-repeat="x in names">
    <td>{{ x.Name }}</td>
    <td>{{ x.Country }}</td>
  </tr>
</table>

</div>

<script>
var app = angular.module('myApp', []);
app.controller('customersCtrl', function($scope, $http) {
    $http.get("/try/angularjs/data/Customers_JSON.php")
    .then(function (result) {
        $scope.names = result.data.records;
    });
});
</script>
```


### 废弃声明 (v1.5)

v1.5 中$http 的 success 和 error 方法已废弃。使用 then 方法替代。

如果你使用的是 v1.5 以下版本，可以使用以下代码：

```javascript
var app = angular.module('myApp', []);
app.controller('customersCtrl', function($scope, $http) {
    $http.get("/try/angularjs/data/Customers_JSON.php")
    .success(function (response) {$scope.names = response.records;});
});
```


## Customers_JSON.php 文件代码：

```html
<?php
echo <<<EOT
{
"records":[
{"Name":"Alfreds Futterkiste","City":"Berlin","Country":"Germany"},
{"Name":"Ana Trujillo Emparedados y helados","City":"México D.F.","Country":"Mexico"},
{"Name":"Antonio Moreno Taquería","City":"México D.F.","Country":"Mexico"},
{"Name":"Around the Horn","City":"London","Country":"UK"},
{"Name":"B's Beverages","City":"London","Country":"UK"},
{"Name":"Berglunds snabbköp","City":"Luleå","Country":"Sweden"},
{"Name":"Blauer See Delikatessen","City":"Mannheim","Country":"Germany"},
{"Name":"Blondel père et fils","City":"Strasbourg","Country":"France"},
{"Name":"Bólido Comidas preparadas","City":"Madrid","Country":"Spain"},
{"Name":"Bon app'","City":"Marseille","Country":"France"},
{"Name":"Bottom-Dollar Marketse","City":"Tsawassen","Country":"Canada"},
{"Name":"Cactus Comidas para llevar","City":"Buenos Aires","Country":"Argentina"},
{"Name":"Centro comercial Moctezuma","City":"México D.F.","Country":"Mexico"},
{"Name":"Chop-suey Chinese","City":"Bern","Country":"Switzerland"},
{"Name":"Comércio Mineiro","City":"São Paulo","Country":"Brazil"}
]
}
EOT;
?>
```


## 使用 CSS 样式

为了让页面更加美观，我们可以在页面中使用CSS：


## CSS 样式


## 使用 orderBy 过滤器

排序显示，可以使用 orderBy 过滤器:


## AngularJS 实例


## 使用 uppercase 过滤器

使用 uppercase 过滤器转换为大写:


## AngularJS 实例


## 显示序号 ($index)

表格显示序号可以在 <td> 中添加 $index:


## AngularJS 实例


## 使用 $even 和 $odd


## AngularJS 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AngularJS 表格` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
