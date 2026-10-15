# jQuery Mobile：jQuery Mobile 按钮

- 来源：[jQuery Mobile 按钮](https://www.runoob.com/jquerymobile/jquerymobile-buttons.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：学习笔记
- 章节序号：3336

## 本章内容

Mobile 应用程序是建立在您想要显示的简单的点击事物上。


## 在 jQuery Mobile 中创建按钮

在 jQuery Mobile 中，按钮可通过三种方式创建：

- 使用 <button> 元素
- 使用 <input> 元素
- 使用带有 data-role="button" 的 <a> 元素


## <button>


## <input>


## <a>


## 导航按钮

如需通过按钮在页面间进行链接，请使用带有 data-role="button" 属性的 <a> 元素：


## 实例


## 内联按钮

默认情况下，按钮占满整个屏幕宽度。如果你想要一个仅是与内容一样宽的按钮，或者如果您想要并排显示两个或多个按钮，请添加 data-inline="true"：


## 实例


## 组合按钮

jQuery Mobile 提供了一个简单的方法来将按钮组合在一起。

请把 data-role="controlgroup" 属性和 data-type="horizontal|vertical" 一起使用来规定是否水平或垂直组合按钮：


## 实例


## 后退按钮

如需创建后退按钮，请使用 data-rel="back" 属性（这会忽略锚的 href 值）：


## 实例


## 更多链接按钮实例

更完整的CSS类，请查看我们的 jQuery Mobile CSS 类参考手册。

下一章演示如何在按钮上加上图标。


## 复习重点

- 能说明 `jQuery Mobile 按钮` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
