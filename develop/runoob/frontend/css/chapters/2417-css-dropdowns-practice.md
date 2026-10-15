# CSS：CSS 下拉菜单

- 来源：[CSS 下拉菜单](https://www.runoob.com/css/css-dropdowns.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2417

## 本章内容

使用 CSS 创建一个鼠标移动上去后显示下拉菜单的效果。


## 下拉菜单实例


### 实例演示 1

菜鸟教程

www.runoob.com


### 实例演示 2


### 实例演示 3


## 基本下拉菜单

当鼠标移动到指定元素上时，会出现下拉菜单。


### 实例

```html
<style>
.dropdown {
  position: relative;
  display: inline-block;
}
.dropdown-content {
  display: none;
  position: absolute;
  background-color: #f9f9f9;
  min-width: 160px;
  box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
  padding: 12px 16px;
}
.dropdown:hover .dropdown-content {
  display: block;
}
</style>
```

```html
<div class="dropdown">
  <span>鼠标移动到我这！</span>
  <div class="dropdown-content">
    <p>菜鸟教程</p>
    <p>www.runoob.com</p>
  </div>
</div>
```


### 实例解析

HTML 部分：

我们可以使用任何的 HTML 元素来打开下拉菜单，如：<span>, 或 a <button> 元素。

使用容器元素 (如： <div>) 来创建下拉菜单的内容，并放在任何你想放的位置上。

使用 <div> 元素来包裹这些元素，并使用 CSS 来设置下拉内容的样式。

CSS 部分：

.dropdown 类使用 position:relative, 这将设置下拉菜单的内容放置在下拉按钮 (使用 position:absolute) 的右下角位置。

.dropdown-content 类中是实际的下拉菜单。默认是隐藏的，在鼠标移动到指定元素后会显示。 注意 min-width 的值设置为 160px。你可以随意修改它。 注意: 如果你想设置下拉内容与下拉按钮的宽度一致，可设置 width 为 100% ( overflow:auto 设置可以在小尺寸屏幕上滚动)。

我们使用 box-shadow 属性让下拉菜单看起来像一个"卡片"。

:hover 选择器用于在用户将鼠标移动到下拉按钮上时显示下拉菜单。


## 下拉菜单

创建下拉菜单，并允许用户选取列表中的某一项：

这个实例类似前面的实例，当我们在下拉列表中添加了链接，并设置了样式：


### 实例


## 下拉内容对齐方式


### float:left;


### float:right;

如果你想设置右浮动的下拉菜单内容方向是从右到左，而不是从左到右，可以添加以下代码 right: 0;


### 实例


## 更多实例

图片下拉 该实例演示了如何如何在下拉菜单中添加图片。

导航条下拉 该实例演示了如何在导航条上添加下拉菜单。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS 下拉菜单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
