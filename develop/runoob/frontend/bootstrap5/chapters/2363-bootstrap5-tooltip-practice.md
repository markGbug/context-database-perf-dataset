# Bootstrap5：Bootstrap5 提示框

- 来源：[Bootstrap5 提示框](https://www.runoob.com/bootstrap5/bootstrap5-tooltip.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：练习笔记
- 章节序号：2363

## 本章内容

提示框是一个小小的弹窗，在鼠标移动到元素上显示，鼠标移到元素外就消失。


## 如何创建提示框

通过向元素添加 data-bs-toggle="tooltip" 来来创建提示框。

title 属性的内容为提示框显示的内容：

```html
<button type="button" class="btn btn-primary" data-bs-toggle="tooltip" title="我是提示内容!">鼠标移动到我这</button>
```

注意: 提示框要写在 JavaScript 的初始化代码里: 然后在指定的元素上调用 tooltip() 方法。

以下实例可以在文档的任何地方使用提示框：


## 实例

```javascript
var tooltipTriggerList = [].slice.call(document.querySelectorAll('[data-bs-toggle="tooltip"]'))
var tooltipList = tooltipTriggerList.map(function (tooltipTriggerEl) {
  return new bootstrap.Tooltip(tooltipTriggerEl)
})
```


## 指定提示框的位置

默认情况下提示框显示在元素上方。

可以使用 data-bs-placement 属性来设定提示框显示的方向: top, bottom, left 或 right:


## 实例

```html
<a href="#" data-bs-toggle="tooltip" data-bs-placement="top" title="我是提示内容!">鼠标移动到我这</a>
<a href="#" data-bs-toggle="tooltip" data-bs-placement="bottom" title="我是提示内容!">鼠标移动到我这</a>
<a href="#" data-bs-toggle="tooltip" data-bs-placement="left" title="我是提示内容!">鼠标移动到我这</a>
<a href="#" data-bs-toggle="tooltip" data-bs-placement="right" title="我是提示内容!">鼠标移动到我这</a>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap5 提示框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
