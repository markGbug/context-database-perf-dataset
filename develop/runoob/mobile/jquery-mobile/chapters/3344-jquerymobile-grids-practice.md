# jQuery Mobile：jQuery Mobile 网格

- 来源：[jQuery Mobile 网格](https://www.runoob.com/jquerymobile/jquerymobile-grids.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：练习笔记
- 章节序号：3344

## 本章内容

## jQuery Mobile 网格布局

jQuery Mobile 提供了一套基于 CSS 的分列布局。然而，在移动设备上，由于考虑手机的屏幕宽度狭窄，一般不建议使用分栏分列布局。

但有时您想要将较小的元素（如按钮或导航标签）并排地排列在一起，就像是在一个表格中一样。这种情况下，推荐使用分列布局。

网格中的列是等宽的（合计是 100%），没有边框、背景、margin 或 padding。

这里有四种布局网格可供使用：


## 自定义网格

通过使用CSS，您可以自定义列块：


## 实例

您也可以通过使用内嵌样式来自定义块：

```html
<div class="ui-block-a" style="border: 1px solid black;"><span>Text..</span></div>
```


## 多行

在列中也可以有多个行。

注意：ui-block-a-class 总是创建一个新行：


## 实例


## 响应式网格

在小屏幕中，不建议一行中并排太多按钮（文本会缩短）。

我们在容器使用 ui-responsive 类来创建响应式网格：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery Mobile 网格` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
