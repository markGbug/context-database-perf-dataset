# Bootstrap5：Bootstrap5 Flex（弹性）布局

- 来源：[Bootstrap5 Flex](https://www.runoob.com/bootstrap5/bootstrap5-flex.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：练习笔记
- 章节序号：2369

## 本章内容

Bootstrap5 通过 flex 类来控制页面的布局。


## 弹性盒子(flexbox)

Bootstrap 3 与 Bootstrap 4/5 最大的区别就是 Bootstrap 4/5 使用弹性盒子来布局，而不是使用浮动来布局。

弹性盒子是 CSS3 的一种新的布局模式，更适合响应式的设计，如果你还不了解 flex，可以阅读我们的 CSS3 弹性盒子(Flex Box) 教程

注意：IE9 及其以下版本不支持弹性盒子，所以如果你需要兼容 IE8-9，请使用 Bootstrap 3。

以下实例使用 d-flex 类创建一个弹性盒子容器，并设置三个弹性子元素：


## 实例

```html
<div class="d-flex p-3 bg-secondary text-white">
  <div class="p-2 bg-info">Flex item 1</div>
  <div class="p-2 bg-warning">Flex item 2</div>
  <div class="p-2 bg-primary">Flex item 3</div>
</div>
```

创建显示在同一行上的弹性盒子容器可以使用 d-inline-flex 类:


## 实例

```html
<div class="d-inline-flex p-3 bg-secondary text-white">
  <div class="p-2 bg-info">Flex item 1</div>
  <div class="p-2 bg-warning">Flex item 2</div>
  <div class="p-2 bg-primary">Flex item 3</div>
</div>
```


## 水平方向

.flex-row 可以设置弹性子元素水平显示，这是默认的。

使用 .flex-row-reverse 类用于设置右对齐显示，即与 .flex-row 方向相反。


## 实例

```html
<div class="d-flex flex-row bg-secondary">
  <div class="p-2 bg-info">Flex item 1</div>
  <div class="p-2 bg-warning">Flex item 2</div>
  <div class="p-2 bg-primary">Flex item 3</div>
</div>

<div class="d-flex flex-row-reverse bg-secondary">
  <div class="p-2 bg-info">Flex item 1</div>
  <div class="p-2 bg-warning">Flex item 2</div>
  <div class="p-2 bg-primary">Flex item 3</div>
</div>
```


## 垂直方向

.flex-column 类用于设置弹性子元素垂直方向显示, .flex-column-reverse 用于翻转子元素：


## 实例

```html
<div class="d-flex flex-column">
  <div class="p-2 bg-info">Flex item 1</div>
  <div class="p-2 bg-warning">Flex item 2</div>
  <div class="p-2 bg-primary">Flex item 3</div>
</div>

<div class="d-flex flex-column-reverse">
  <div class="p-2 bg-info">Flex item 1</div>
  <div class="p-2 bg-warning">Flex item 2</div>
  <div class="p-2 bg-primary">Flex item 3</div>
</div>
```


## 内容排列

.justify-content-* 类用于修改弹性子元素的排列方式，* 号允许的值有：start (默认), end, center, between 或 around:


## 实例

```html
<div class="d-flex justify-content-start">...</div>
<div class="d-flex justify-content-end">...</div>
<div class="d-flex justify-content-center">...</div>
<div class="d-flex justify-content-between">...</div>
<div class="d-flex justify-content-around">...</div>
```


## 等宽

.flex-fill 类强制设置各个弹性子元素的宽度是一样的:


## 实例

```html
<div class="d-flex">
  <div class="p-2 bg-info flex-fill">Flex item 1</div>
  <div class="p-2 bg-warning flex-fill">Flex item 2</div>
  <div class="p-2 bg-primary flex-fill">Flex item 3</div>
</div>
```


## 扩展

.flex-grow-1 用于设置子元素使用剩下的空间。以下实例中前面两个子元素只设置了它们所需要的空间，最后一个获取剩余空间。 :


## 实例

```html
<div class="d-flex">
  <div class="p-2 bg-info">Flex item 1</div>
  <div class="p-2 bg-warning">Flex item 2</div>
  <div class="p-2 bg-primary flex-grow-1">Flex item 3</div>
</div>
```

提示: 使用 .flex-shrink-1 用于设置子元素的收缩规则。


## 排序

.order 类可以设置弹性子元素的排序，从 .order-1 到 .order-12，数字越低权重越高( .order-1 排在 .order-2 之前) :


## 实例

```html
<div class="d-flex bg-secondary">
  <div class="p-2 bg-info order-3">Flex item 1</div>
  <div class="p-2 bg-warning order-2">Flex item 2</div>
  <div class="p-2 bg-primary order-1">Flex item 3</div>
</div>
```


## 外边距

.ms-auto 类可以设置子元素右外边距为 auto，即 margin-right: auto!important;，.me-auto 类可以设置子元素左外边距为 auto，即 margin-left: auto!important;:


## 实例

```html
<div class="d-flex mb-3 bg-secondary">
  <div class="p-2 ms-auto bg-info">Flex item 1</div>
  <div class="p-2 bg-warning">Flex item 2</div>
  <div class="p-2 bg-primary">Flex item 3</div>
</div>
<div class="d-flex mb-3 bg-secondary">
  <div class="p-2  bg-info">Flex item 1</div>
  <div class="p-2 bg-warning">Flex item 2</div>
  <div class="p-2 me-auto bg-primary">Flex item 3</div>
</div>
```


## 包裹

弹性容器中包裹子元素可以使用以下三个类： .flex-nowrap (默认), .flex-wrap 或 .flex-wrap-reverse。设置 flex 容器是单行或者多行。


## 实例

```html
<div class="d-flex flex-wrap">..</div>

<div class="d-flex flex-wrap-reverse">..</div>

<div class="d-flex flex-nowrap">..</div>
```


## 内容对齐

我们可以使用 .align-content-* 来控制在垂直方向上如何去堆叠子元素，包含的值有：.align-content-start (默认), .align-content-end, .align-content-center, .align-content-between, .align-content-around 和 .align-content-stretch。

这些类在只有一行的弹性子元素中是无效的。


## 实例

```html
<div class="d-flex flex-wrap align-content-start">..</div>

<div class="d-flex flex-wrap align-content-end">..</div>

<div class="d-flex flex-wrap align-content-center">..</div>

<div class="d-flex flex-wrap align-content-around">..</div>

<div class="d-flex flex-wrap align-content-stretch">..</div>
```


## 子元素对齐

如果要设置单行的子元素对齐可以使用 .align-items-* 类来控制，包含的值有：.align-items-start, .align-items-end, .align-items-center, .align-items-baseline, 和 .align-items-stretch (默认)。


## 实例

```html
<div class="d-flex align-items-start">..</div>

<div class="d-flex align-items-end">..</div>

<div class="d-flex align-items-center">..</div>

<div class="d-flex align-items-around">..</div>

<div class="d-flex align-items-stretch">..</div>
```


## 指定子元素对齐

如果要设置指定子元素对齐对齐可以使用 .align-self-* 类来控制，包含的值有：.align-self-start, .align-self-end, .align-self-center, .align-self-baseline, 和 .align-self-stretch (默认)。


## 后续章节

- 实例
- 响应式 flex 类

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap5 Flex` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
