# Bootstrap4：Bootstrap4 弹出框

- 来源：[Bootstrap4 弹出框](https://www.runoob.com/bootstrap4/bootstrap4-popover.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：练习笔记
- 章节序号：2333

## 本章内容

弹出框控件类似于提示框，它在鼠标点击到元素后显示，与提示框不同的是它可以显示更多的内容。


## 如何创建弹出框

通过向元素添加 data-toggle="popover" 来来创建弹出框。

title 属性的内容为弹出框的标题，data-content 属性显示了弹出框的文本内容：

```html
<a href="#" data-toggle="popover" title="弹出框标题" data-content="弹出框内容">多次点我</a>
```

注意: 弹出框要写在 jQuery 的初始化代码里: 然后在指定的元素上调用 popover() 方法。

以下实例可以在文档的任何地方使用弹出框：


## 实例

```text
$(document).ready(function(){
    $('[data-toggle="popover"]').popover();
});
```


## 指定弹出框的位置

默认情况下弹出框显示在元素右侧。

可以使用 data-placement 属性来设定弹出框显示的方向: top, bottom, left 或 right:


## 实例

```html
<a href="#" title="Header" data-toggle="popover" data-placement="top" data-content="Content">点我</a>
<a href="#" title="Header" data-toggle="popover" data-placement="bottom" data-content="Content">点我</a>
<a href="#" title="Header" data-toggle="popover" data-placement="left" data-content="Content">点我</a>
<a href="#" title="Header" data-toggle="popover" data-placement="right" data-content="Content">点我</a>
```

按钮中使用:


## 实例

```html
<button type="button" class="btn btn-secondary" data-container="body" data-toggle="popover" data-placement="top" data-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus.">
  Popover on top
</button>

<button type="button" class="btn btn-secondary" data-container="body" data-toggle="popover" data-placement="right" data-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus.">
  Popover on right
</button>

<button type="button" class="btn btn-secondary" data-container="body" data-toggle="popover" data-placement="bottom" data-content="Vivamus
sagittis lacus vel augue laoreet rutrum faucibus.">
  Popover on bottom
</button>

<button type="button" class="btn btn-secondary" data-container="body" data-toggle="popover" data-placement="left" data-content="Vivamus sagittis lacus vel augue laoreet rutrum faucibus.">
  Popover on left
</button>
```


## 关闭弹出框

默认情况下，弹出框在再次点击指定元素后就会关闭，你可以使用 data-trigger="focus" 属性来设置在鼠标点击元素外部区域来关闭弹出框：


## 实例

```html
<a href="#" title="取消弹出框" data-toggle="popover" data-trigger="focus" data-content="点击文档的其他地方关闭我">点我</a>
```

提示:如果你想实现在鼠标移动到元素上显示，移除后消失的效果，可以使用 data-trigger 属性，并设置值为 "hover":


## 实例

```html
<a href="#" title="Header" data-toggle="popover" data-trigger="hover" data-content="一些内容">鼠标移动到我这</a>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap4 弹出框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
