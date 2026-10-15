# Foundation：Foundation 图片

- 来源：[Foundation 图片](https://www.runoob.com/foundation/foundation-images.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：学习笔记
- 章节序号：2533

## 本章内容

Foundation 提供了响应式的图片，可以创建缩略图和图片弹窗：


## 缩略图

在 <img> 元素外添加 <a> 元素将图片作为一个锚链接。

在 <a> 标签中添加 .th 类将图片设置为缩略图。 鼠标移动到上面会显示一个浅蓝色外框:


### 实例


## 圆角图片

我们可以在 .th 类添加 .radius 类来设置圆角缩略图：


### 实例


## 简洁的弹窗

Foundation 可以很容易实现图片弹窗。

要创建一个弹窗可以在 <ul> 元素上添加 .clearing-thumbs 类及 data-clearing 属性。在 <ul> 内添加图片列表。

注意: 图片弹窗需要 JavaScript。所以使用它前需要初始化 Foundation JS。


### 实例


## 图片文本描述

可以添加 data-caption 属性到每个图片来设置图片的描述:


### 实例


## 只显示一张缩略图

当你需要实现只显示一张缩略图时你可以在 <ul> 中使用 .clearing-feature 类并在<li> 中使用 .clearing-featured-img 类。


### 实例


## 复习重点

- 能说明 `Foundation 图片` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
