# CSS：响应式 Web 设计 - Viewport

- 来源：[Viewport](https://www.runoob.com/css/css-rwd-viewport.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2453

## 本章内容

## 什么是 Viewport?

viewport 是用户网页的可视区域。

viewport 翻译为中文可以叫做"视区"。

手机浏览器是把页面放在一个虚拟的"窗口"（viewport）中，通常这个虚拟的"窗口"（viewport）比屏幕宽，这样就不用把每个网页挤到很小的窗口中（这样会破坏没有针对手机浏览器优化的网页的布局），用户可以通过平移和缩放来看网页的不同部分。


## 设置 Viewport

一个常用的针对移动网页优化过的页面的 viewport meta 标签大致如下：

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

- width：控制 viewport 的大小，可以指定的一个值，如 600，或者特殊的值，如 device-width 为设备的宽度（单位为缩放为 100% 时的 CSS 的像素）。
- height：和 width 相对应，指定高度。
- initial-scale：初始缩放比例，也即是当页面第一次 load 的时候缩放比例。
- maximum-scale：允许用户缩放到的最大比例。
- minimum-scale：允许用户缩放到的最小比例。
- user-scalable：用户是否可以手动缩放。

以下实例演示了使用viewport和没使用viewport在移动端上的效果：


### 实例1、没有添加 viewport：点击查看


### 实例2、添加 viewport：点击查看

如果你在平板电脑或手机上访问，可以直接点击查看效果。


## 复习重点

- 能说明 `Viewport` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
