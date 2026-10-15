# AngularJS：AngularJS 过滤器

- 来源：[AngularJS 过滤器](https://www.runoob.com/angularjs/angularjs-filters.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：练习笔记
- 章节序号：2284

## 本章内容

过滤器可以使用一个管道字符（|）添加到表达式和指令中。


## AngularJS 过滤器

AngularJS 过滤器可用于转换数据：


## 表达式中添加过滤器

过滤器可以通过一个管道字符（|）和一个过滤器添加到表达式中。.

(下面的两个实例，我们将使用前面章节中提到的 person 控制器)

uppercase 过滤器将字符串格式化为大写：


## AngularJS 实例

lowercase 过滤器将字符串格式化为小写：


## AngularJS 实例


## currency 过滤器

currency 过滤器将数字格式化为货币格式：


## AngularJS 实例


## 向指令添加过滤器

过滤器可以通过一个管道字符（|）和一个过滤器添加到指令中。

orderBy 过滤器根据表达式排列数组：


## AngularJS 实例


## 过滤输入

输入过滤器可以通过一个管道字符（|）和一个过滤器添加到指令中，该过滤器后跟一个冒号和一个模型名称。

filter 过滤器从数组中选择一个子集：


## AngularJS 实例


## 自定义过滤器

以下实例自定义一个过滤器 reverse，将字符串反转：


## AngularJS 实例

```javascript
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.msg = "Runoob";
});
app.filter('reverse', function() { //可以注入依赖
    return function(text) {
        return text.split("").reverse().join("");
    }
});
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `AngularJS 过滤器` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
