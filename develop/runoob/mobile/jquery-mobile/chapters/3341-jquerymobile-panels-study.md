# jQuery Mobile：jQuery Mobile 面板

- 来源：[jQuery Mobile 面板](https://www.runoob.com/jquerymobile/jquerymobile-panels.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：学习笔记
- 章节序号：3341

## 本章内容

jQuery Mobile 中的面板会在屏幕的左侧向右侧划出。

通过向指定 id 的 <div> 元素添加 data-role="panel" 属性来创建面板。

在 <div> 中添加 HTML 标记来显示你的面板内容：

```html
<div data-role="panel" id="myPanel">
  <h2>面板标题..</h2>
  <p>文本内容..</p>
</div>
```

注意： panel 标记必须置于头部、内容、底部组成的页面之前或之后。

要访问面板，需要创建一个指向面板 <div> id 的链接，点击该链接即可打开面板:

```html
<a href="#myPanel" class="ui-btn ui-btn-inline">打开面板</a>
```

简单的面板实例


## 实例


## 关闭面板

你可以通过点击面板外部区域或按下 Esc 键或滑动来关闭面板。你可以通过使用 data-* 属性来禁用滑动和点击来关闭面板：

你可以使用按钮来关闭面板：仅需要在面板的 <div> 中添加 data-rel="close" 属性。 从性能上考虑，我们需要键关闭链接的 href 属性指向页面的 ID 。


## 实例


## 面板展示

你可以通过使用 data-display 属性来控制面板的展示方式:


## 实例


## 面板定位

默认情况下，面板会显示在屏幕的左侧。如果想让面板出现在屏幕的右侧，可以指定 data-position="right" 属性。


## 实例

你可以指定面板的内容根据页面滚动而滚动。默认情况下面板是随着页面一起滚动的（但是面板的内容仍然位于页面顶部）。如果你需要实现面板内容固定不随页面滚动而滚动，可以在面板添加 the data-position-fixed="true" 属性:


## 实例


## 复习重点

- 能说明 `jQuery Mobile 面板` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
