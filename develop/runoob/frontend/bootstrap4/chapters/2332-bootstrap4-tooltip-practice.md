# Bootstrap4：Bootstrap4 提示框

- 来源：[Bootstrap4 提示框](https://www.runoob.com/bootstrap4/bootstrap4-tooltip.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：练习笔记
- 章节序号：2332

## 本章内容

提示框是一个小小的弹窗，在鼠标移动到元素上显示，鼠标移到元素外就消失。


## 如何创建提示框

通过向元素添加 data-toggle="tooltip" 来来创建提示框。

title 属性的内容为提示框显示的内容：

```html
<a href="#" data-toggle="tooltip" title="我是提示内容!">鼠标移动到我这</a>
```

注意: 提示框要写在 jQuery 的初始化代码里: 然后在指定的元素上调用 tooltip() 方法。

以下实例可以在文档的任何地方使用提示框：


## 实例

```text
$(document).ready(function(){
    $('[data-toggle="tooltip"]').tooltip();
});
```


## 指定提示框的位置

默认情况下提示框显示在元素上方。

可以使用 data-placement 属性来设定提示框显示的方向: top, bottom, left 或 right:


## 实例

```html
<a href="#" data-toggle="tooltip" data-placement="top" title="我是提示内容!">鼠标移动到我这</a>
<a href="#" data-toggle="tooltip" data-placement="bottom" title="我是提示内容!">鼠标移动到我这</a>
<a href="#" data-toggle="tooltip" data-placement="left" title="我是提示内容!">鼠标移动到我这</a>
<a href="#" data-toggle="tooltip" data-placement="right" title="我是提示内容!">鼠标移动到我这</a>
```

在按钮中使用:


## 实例

```html
<button type="button" class="btn btn-secondary" data-toggle="tooltip" data-placement="top" title="Tooltip on top">
  Tooltip on top
</button>
<button type="button" class="btn btn-secondary" data-toggle="tooltip" data-placement="right" title="Tooltip on right">
  Tooltip on right
</button>
<button type="button" class="btn btn-secondary" data-toggle="tooltip" data-placement="bottom" title="Tooltip on bottom">
  Tooltip on bottom
</button>
<button type="button" class="btn btn-secondary" data-toggle="tooltip" data-placement="left" title="Tooltip on left">
  Tooltip on left
</button>
```

提示内容添加 HTML 标签，设置 data-html="true"，内容放在 title 标签里头:


## 实例

```html
<button type="button" class="btn btn-secondary" data-toggle="tooltip" data-html="true" title="<em>Tooltip</em> <u>with</u> <b>HTML</b>">
  Tooltip with HTML
</button>
```

禁用按钮：


## 实例

```html
<span class="d-inline-block" tabindex="0" data-toggle="tooltip" title="Disabled tooltip">
  <button class="btn btn-primary" style="pointer-events: none;" type="button" disabled>Disabled button</button>
</span>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap4 提示框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
