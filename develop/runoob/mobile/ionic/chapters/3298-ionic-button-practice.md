# Ionic：ionic 按钮

- 来源：[ionic 按钮](https://www.runoob.com/ionic/ionic-button.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3298

## 本章内容

按钮是移动app不可或缺的一部分，不同风格的app，需要的不同按钮的样式。

默认情况下，按钮显示样式为：display: inline-block。

```html
<button class="button">
  Default
</button>

<button class="button button-light">
  button-light
</button>

<button class="button button-stable">
  button-stable
</button>

<button class="button button-positive">
  button-positive
</button>

<button class="button button-calm">
  button-calm
</button>

<button class="button button-balanced">
  button-balanced
</button>

<button class="button button-energized">
  button-energized
</button>

<button class="button button-assertive">
  button-assertive
</button>

<button class="button button-royal">
  button-royal
</button>

<button class="button button-dark">
  button-dark
</button>
```

尝试一下 »

button-block 样式按钮显示为：display: block，它将完全填充父元素的宽度，包含了内边距属性padding。

```html
<button class="button button-block button-positive">
  Block Button
</button>
```

尝试一下 »

使用 button-full 类，可以让按钮显示完全宽度，且不包含内边距padding。

```html
<button class="button button-full button-positive">
  Full Width Block Button
</button>
```

尝试一下 »


## 不同大小的按钮

button-large 设置为大按钮，button-small 设置为小按钮。

```html
<button class="button button-small button-assertive">
  Small Button
</button>
<button class="button button-large button-positive">
  Large Button
</button>
```

尝试一下 »


## 无背景按钮

button-outline 设置背景为透明。

```html
<button class="button button-outline button-positive">
  Outlined Button
</button>
```

尝试一下 »


## 无背景与边框按钮

button-clear 设置按钮背景为透明，且无边框。

```html
<button class="button button-clear button-positive">
  Clear Button
</button>
```

尝试一下 »


## 图标按钮

我们可以在按钮上添加图标。

```html
<button class="button icon-left ion-home">Home</button>

<button class="button icon-left ion-star button-positive">Favorites</button>

<a class="button icon-right ion-chevron-right button-calm">Learn More</a>

<a class="button icon-left ion-chevron-left button-clear button-dark">Back</a>

<button class="button icon ion-gear-a"></button>

<a class="button button-icon icon ion-settings"></a>

<a class="button button-outline icon-right ion-navicon button-balanced">Reorder</a>
```

尝试一下 »


## 头部/底部添加按钮

头部/底部可以添加按钮，按钮的样式根据头部/底部来设定，所以你不需要为按钮添加额外的样式。

```html
<div class="bar bar-header">
  <button class="button icon ion-navicon"></button>
  <h1 class="title">Header Buttons</h1>
  <button class="button">Edit</button>
</div>
```

尝试一下 »

button-clear 类可以设置无背景和边框的头部/底部按钮。

```html
<div class="bar bar-header">
  <button class="button button-icon icon ion-navicon"></button>
  <div class="h1 title">Header Buttons</div>
  <button class="button button-clear button-positive">Edit</button>
</div>
```

尝试一下 »


## 按钮栏

```html
<div class="button-bar">
  <a class="button">First</a>
  <a class="button">Second</a>
  <a class="button">Third</a>
</div>
```

尝试一下 »


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic 按钮` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
