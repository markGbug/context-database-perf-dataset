# jQuery Mobile：jQuery Mobile 过渡

- 来源：[jQuery Mobile 过渡](https://www.runoob.com/jquerymobile/jquerymobile-transitions.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：学习笔记
- 章节序号：3335

## 本章内容

jQuery Mobile 包含 CSS3 效果让您选择页面打开的方式。


## jQuery Mobile 页面切换效果

jQuery Mobile 提供了各种页面切换到下一个页面的效果。

注意：为了实现页面切换效果，浏览器必须支持 CSS3 3D 切换：

表格中的数字为支持 3D 旋转的最小浏览器版本号。

页面过渡效果可被应用于任何使用 data-transition 属性的链接或表单：

页面切换效果可被应用于任何使用 data-transition 属性的链接或表单提交：

```html
<a href="#anylink" data-transition="slide">切换到第二个页面</a>
```

下面的表格显示了通过使用 data-transition 属性后可用的页面切换：

提示：上面的所有效果支持后退行为。例如，如果您想要页面从左向右滑动，而不是从右向左滑动，请使用带有 "reverse" 值的 data-direction 属性。在后退按钮上这是默认的。


## 实例


## 复习重点

- 能说明 `jQuery Mobile 过渡` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
