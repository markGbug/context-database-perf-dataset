# jQuery Mobile：jQuery Mobile Data 属性

- 来源：[jQuery Mobile Data 属性](https://www.runoob.com/jquerymobile/jquerymobile-ref-data.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：学习笔记
- 章节序号：3358

## 本章内容

## jQuery Data 属性

jQuery Mobile 使用 HTML5 data-* 属性来为移动设备创建更具触摸友好性和吸引性的外观。

在下面的参考列表中，粗体显示的值为默认值。


## 按钮

在1.4 版本以后已废弃。使用 CSS 类 替代。带有 data-role="button" 的超链接。button 元素、工具栏中的链接以及 input 字段都会自动渲染成按钮样式，不需要添加 data-role="button"。


## 复选框

带有 type="checkbox" 的成双成对的 label 和 input。它们会被自动渲染成按钮样式，data-role 不是必需的。


## 可折叠块

在带有 data-role="collapsible" 的容器内部的后跟任意 HTML 标记的标题元素。


## 可折叠集合

在带有 data-role="collapsible-set" 的容器内部的可折叠内容块。


## 内容

在 1.4 版本已废弃, 1.5 版本后不再支持。 使用 data-role="content" 的容器。


## 控件组

带有 data-role="controlgroup" 的 <div> 或 <fieldset> 容器。 组合单个类型（基于链接的按钮、单选按钮、复选框、select 元素）的多个按钮样式的 input。对于组合表单复选框和单选按钮，推荐在带有 data-role="fieldcontain" 的 <div> 内使用 <fieldset> 容器来改进标签样式。


## 对话框

带有 data-role="dialog" 的容器或带有 data-rel="dialog" 的链接。


## 增强

带有 data-enhance="false" 或 data-ajax="false" 的容器。

注意：data-enhance="false" 必须与 $.mobile.ignoreContentEnabled=true" 一同使用来阻止 jQuery Mobile 自动渲染页面。

当 $.mobile.ignoreContentEnabled 设置为 true 时，data-ajax="false" 容器内的任何链接或表单元素将会被框架的导航功能忽略。


## 域容器

1.4 版本后已废弃，在 1.5 版本后不再支持，将使用 class="ui-fieldcontain 替代"。 包裹在 label/form 元素对，并带有 data-role="fieldcontain" 的容器。


## 固定工具栏

带有 data-role="header" 或 data-role="footer"，并带有 data-position="fixed" 属性的容器。


## 翻转拨动开关

一个带有 data-role="slider" 的 <select> 元素和两个 <option> 元素。


## 尾部栏

带有 data-role="footer" 的容器。

注意：如需启用全屏定位，请使用 data-position="fixed"，然后添加 data-fullscreen 属性到元素上。


## 头部栏

带有 data-role="header" 的容器。

注意：如需启用全屏定位，请使用 data-position="fixed"，然后添加 data-fullscreen 属性到元素上。


## 链接

所有的链接，包含那些带有 data-role="button" 的链接和表单提交按钮。


## 列表

带有 data-role="listview" 的 <ol> 或 <ul>。


## 列表项

带有 data-role="listview" 的 <ol> 或 <ul> 内的 <li>。

注意：data-icon 属性只作用于带有链接的列表项。


## 导航栏

带有 data-role="navbar" 容器内部的 <li> 元素。


## 页面

带有 data-role="page" 的容器。


## 弹窗

带有 data-role="popup" 的容器。

带有 data-rel="popup" 的锚：


## 单选按钮

带有 type="radio" 的成双成对的 label 和 input。它们会被自动渲染程按钮样式，data-role 不是必需的。


## 选择

所有的 <select> 元素。这些会被自动渲染成按钮样式，date-role 是不必需的。


## 滑动块

带有 type="range" 的输入框。这些会被自动渲染成按钮样式，date-role 是不必需的。


## 文本输入框 & 文本输入域

带有 type="text|search|etc." 的 input 或 textarea 元素。这些会被自动渲染成按钮样式，date-role 是不必需的。


## 复习重点

- 能说明 `jQuery Mobile Data 属性` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
