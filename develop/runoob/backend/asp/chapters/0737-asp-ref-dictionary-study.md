# ASP：ASP Dictionary 对象

- 来源：[ASP Dictionary](https://www.runoob.com/asp/asp-ref-dictionary.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：学习笔记
- 章节序号：0737

## 本章内容

Dictionary 对象用于在名称/值对中存储信息。


## 尝试一下 - 实例

指定的键存在吗？ 本例演示如何创建一个 Dictionary 对象，然后使用 Exists 方法来检查指定的键是否存在。

返回一个所有项目的数组 本例演示如何使用 Items 方法来返回一个所有项目的数组。

返回一个所有键的数组 本例演示如何使用 Keys 方法来返回一个所有键的数组。

返回一个项目的值 本例演示如何使用 Item 属性来返回一个项目的值。

设置一个键 本例演示如何使用 Key 属性来在 Dictionary 对象中设置一个键。

返回键/项目对的数量 本例演示如何使用 Count 属性来返回键/项目对的数量。


## Dictionary 对象

Dictionary 对象用于在名称/值对（等同于键和项目）中存储信息。Dictionary 对象看似比数组更为简单，然而，Dictionary 对象却是更令人满意的处理关联数据的解决方案。

比较 Dictionaries 和数组：

- 键用于识别 Dictionary 对象中的项目
- 您无需调用 ReDim 来改变 Dictionary 对象的尺寸
- 当从 Dictionary 中删除一个项目时，其余的项目会自动上移
- Dictionary 不是多维，而数组是多维
- Dictionary 比数组带有更多的内建函数
- Dictionary 在频繁地访问随机元素时，比数组工作得更好
- Dictionary 在根据它们的内容定位项目时，比数组工作得更好

下面的实例创建了一个 Dictionary 对象，并向对象添加了一些键/项目对，然后取回了键 gr 的项目值：

Dictionary 对象的属性和方法描述如下：


### 属性


### 方法


## 复习重点

- 能说明 `ASP Dictionary` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
