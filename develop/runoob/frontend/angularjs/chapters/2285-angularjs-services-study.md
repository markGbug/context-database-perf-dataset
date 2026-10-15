# AngularJS：AngularJS 服务(Service)

- 来源：[AngularJS Service](https://www.runoob.com/angularjs/angularjs-services.html)
- 分类：前端开发
- 技术：AngularJS
- 笔记类型：学习笔记
- 章节序号：2285

## 本章内容

AngularJS 中你可以创建自己的服务，或使用内建服务。


## 什么是服务？

在 AngularJS 中，服务是一个函数或对象，可在你的 AngularJS 应用中使用。

AngularJS 内建了30 多个服务。

有个 $location 服务，它可以返回当前页面的 URL 地址。


### 实例

注意 $location 服务是作为一个参数传递到 controller 中。如果要使用它，需要在 controller 中定义。


## 为什么使用服务?

在很多服务中，比如 $location 服务，它可以使用 DOM 中存在的对象，类似 window.location 对象，但 window.location 对象在 AngularJS 应用中有一定的局限性。

AngularJS 会一直监控应用，处理事件变化， AngularJS 使用 $location 服务比使用 window.location 对象更好。


### $location vs window.location


## $http 服务

$http 是 AngularJS 应用中最常用的服务。 服务向服务器发送请求，应用响应服务器传送过来的数据。


### 实例

使用 $http 服务向服务器请求数据:

以上是一个非常简单的 $http 服务实例，更多 $http 服务应用请查看 AngularJS Http 教程。


## $timeout 服务

AngularJS $timeout 服务对应了 JS window.setTimeout 函数。


### 实例

两秒后显示信息:


## $interval 服务

AngularJS $interval 服务对应了 JS window.setInterval 函数。


### 实例

每一秒显示信息:


## 创建自定义服务

你可以创建自定义服务，链接到你的模块中：

创建名为hexafy 的服务:

要使用自定义服务，需要在定义控制器的时候独立添加，设置依赖关系:


### 实例

使用自定义的的服务 hexafy 将一个数字转换为16进制数:


## 过滤器中，使用自定义服务

当你创建了自定义服务，并连接到你的应用上后，你可以在控制器，指令，过滤器或其他服务中使用它。

在过滤器 myFormat 中使用服务 hexafy:

在对象数组中获取值时你可以使用过滤器：

创建服务 hexafy:


## 复习重点

- 能说明 `AngularJS Service` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
