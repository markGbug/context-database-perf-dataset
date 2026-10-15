# Foundation：Foundation 按钮组

- 来源：[Foundation 按钮组](https://www.runoob.com/foundation/foundation-button-groups.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：学习笔记
- 章节序号：2527

## 本章内容

## 按钮组

Foundation 可以在同一行内创建一系列的按钮。

可以使用 <ul> 元素并添加 .button-group 类来创建按钮组：


### 实例


## 垂直按钮组

垂直按钮组使用 .stack 类来创建。注意，按钮会跨越父元素的整个宽度:


### 实例

.stack-for-small 类用于小尺寸的屏幕，按钮有水平排列变为垂直排列：


### 实例


## 圆角按钮组

按钮组中使用 .radius 和 .round 类为按钮添加圆角效果：


### 实例


## 均匀延展按钮组

.even-num 类用于在按钮组中均匀的分配按钮的宽度并跨越父元素 100% 宽度。

num 为按钮组中按钮的数量，从 1 到 8：


### 实例


## 下拉菜单按钮

下拉菜单按钮可以让用户选取设定好的值：


### 实例


### 实例解析

.dropdown 类创建一个下拉菜单按钮。

使用带有 data-dropdown="id" 属性的按钮或链接打开下拉菜单。

id 值需要与下拉菜单的内容 (id01) 匹配。

在 <ul> 中添加 .f-dropdown 类和 data-dropdown-content 属性来创建下拉菜单的内容。

最后初始化 Foundation JS。


## 分割按钮

我们也可以创建一个分割按钮的下拉菜单。只需要在按钮中添加 .split 类并使用 span 元素生成一个方向箭的按钮：


### 实例


## 复习重点

- 能说明 `Foundation 按钮组` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
