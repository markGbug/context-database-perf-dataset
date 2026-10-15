# CSS：CSS 背景

- 来源：[CSS Backgrounds(背景)](https://www.runoob.com/css/css-background.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2395

## 本章内容

CSS 背景属性用于定义HTML元素的背景。

CSS 属性定义背景效果:

- background-color
- background-image
- background-repeat
- background-attachment
- background-position


## 背景颜色

background-color 属性定义了元素的背景颜色.

页面的背景颜色使用在body的选择器中:


## 实例

CSS中，颜色值通常以以下方式定义:

- 十六进制 - 如："#ff0000"
- RGB - 如："rgb(255,0,0)"
- 颜色名称 - 如："red"

以下实例中, h1, p, 和 div 元素拥有不同的背景颜色:


## 实例


## 背景图像

background-image 属性描述了元素的背景图像.

默认情况下，背景图像进行平铺重复显示，以覆盖整个元素实体.

页面背景图片设置实例:


## 实例

下面是一个例子是一个糟糕的文字和背景图像组合。文本可读性差:


## 实例


## 背景图像 - 水平或垂直平铺

默认情况下 background-image 属性会在页面的水平或者垂直方向平铺。

一些图像如果在水平方向与垂直方向平铺，这样看起来很不协调，如下所示:


## 实例

如果图像只在水平方向平铺 (repeat-x), 页面背景会更好些:


## 实例


## 背景图像- 设置定位与不平铺

让背景图像不影响文本的排版

如果你不想让图像平铺，你可以使用 background-repeat 属性:


## 实例

以上实例中，背景图像与文本显示在同一个位置，为了让页面排版更加合理，不影响文本的阅读，我们可以改变图像的位置。

可以利用 background-position 属性改变图像在背景中的位置:


## 实例


## 背景- 简写属性

在以上实例中我们可以看到页面的背景颜色通过了很多的属性来控制。

为了简化这些属性的代码，我们可以将这些属性合并在同一个属性中.

背景颜色的简写属性为 "background":


## 实例

当使用简写属性时，属性值的顺序为：:

- background-color
- background-image
- background-repeat
- background-attachment
- background-position

以上属性无需全部使用，你可以按照页面的实际需要使用.

这个实例使用了先前介绍的CSS，你可以查看相应实例: CSS 实例


## 更多实例

如何设置固定的背景图像 本例演示如何设置固定的背景图像。图像不会随着页面的其他部分滚动。


## CSS 背景属性


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS Backgrounds(背景)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
