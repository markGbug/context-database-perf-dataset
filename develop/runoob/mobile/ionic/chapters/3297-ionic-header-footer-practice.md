# Ionic：ionic 头部与底部

- 来源：[ionic 头部与底部](https://www.runoob.com/ionic/ionic-header-footer.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3297

## 本章内容

## Header(头部)

Header是固定在屏幕顶部的组件,可以包如标题和左右的功能按钮。

ionic 默认提供了许多种颜色样式，你可以调用不同的样式名，当然也可以自定义一个。


### bar-light

```html
<div class="bar bar-header bar-light">
  <h1 class="title">bar-light</h1>
</div>
```

尝试一下 »


### bar-stable

```html
<div class="bar bar-header bar-stable">
  <h1 class="title">bar-stable</h1>
</div>
```

尝试一下 »


### bar-positive

```html
<div class="bar bar-header bar-positive">
  <h1 class="title">bar-positive</h1>
</div>
```

尝试一下 »


### bar-calm

```html
<div class="bar bar-header bar-calm">
  <h1 class="title">bar-calm</h1>
</div>
```

尝试一下 »


### bar-balanced

```html
<div class="bar bar-header bar-balanced">
  <h1 class="title">bar-balanced</h1>
</div>
```

尝试一下 »


### bar-energized

```html
<div class="bar bar-header bar-energized">
  <h1 class="title">bar-energized</h1>
</div>
```

尝试一下 »


### bar-assertive

```html
<div class="bar bar-header bar-assertive">
  <h1 class="title">bar-assertive</h1>
</div>
```

尝试一下 »


### bar-royal

```html
<div class="bar bar-header bar-royal">
  <h1 class="title">bar-royal</h1>
</div>
```

尝试一下 »


### bar-dark

```html
<div class="bar bar-header bar-dark">
  <h1 class="title">bar-dark</h1>
</div>
```

尝试一下 »


## Sub Header（副标题）

Sub Header同样是固定在顶部，只是是在Header的下面，就算没有写Header这个，Sub Header这个样式也会距离顶部有一个Header的距离。颜色样式同 Header 。

```html
<div class="bar bar-header">
  <h1 class="title">Header</h1>
</div>
<div class="bar bar-subheader">
  <h2 class="title">Sub Header</h2>
</div>
```

尝试一下 »


## Footer(底部)

Footer 是在屏幕的最下方，可以包含多种内容类型。

```html
<div class="bar bar-footer bar-balanced">
  <div class="title">Footer</div>
</div>
```

尝试一下 »

Footer 同上面的 Header，只是把样式名 bar-header 换做 bar-footer 。

```html
<div class="bar bar-footer">
  <button class="button button-clear">Left</button>
  <div class="title">Title</div>
  <button class="button button-clear">Right</button>
</div>
```

尝试一下 »

此外，如果底部没有标题，但是又需要右边的按钮，你需要在右侧按钮添加 pull-right如:

```html
<div class="bar bar-footer">
  <button class="button button-clear pull-right">Right</button>
</div>
```

尝试一下 »


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic 头部与底部` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
