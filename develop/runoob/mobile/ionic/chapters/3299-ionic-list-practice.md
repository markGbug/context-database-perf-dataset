# Ionic：ionic 列表

- 来源：[ionic 列表](https://www.runoob.com/ionic/ionic-list.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：练习笔记
- 章节序号：3299

## 本章内容

列表是一个应用广泛的界面元素，在所有移动app中几乎都会使用到。

列表可以是基本文字、按钮，开关，图标和缩略图等。

列表项可以是任何的HTML元素。容器元素需要list类，每个列表项需要使用item类。

ionList和ionItem可以很容易的支持各种交互方式，比如，滑动编辑，拖动排序，以及删除项。


### 基本用法:

```html
<ul class="list">
    <li class="item">
      ...
    </li>
</ul>
```

尝试一下 »


### 列表分隔符

我们可以使用 item-divider 类来为列表创建分隔符，默认情况下，列表项以不同的背景颜色和字体加粗来区分，但你也可以很容易的定制他。

```html
<div class="list">

  <div class="item item-divider">
    Candy Bars
  </div>

  <a class="item" href="#">
    Butterfinger
  </a>

  ...

</div>
```

尝试一下 »


## 带图标列表

我们可以在列表项的左侧或右侧指定图标。

使用 item-icon-left 图标在左侧， item-icon-right 设置图标在右侧。如果你需要在两边都有图标，则两个类都添加上即可。

以下实例中，我们在列表项中使用了 <a> 标签，使得每个列表项可点击。

列表项在使用 <a>或<button> 元素时，如果右侧未添加图标，则会自动添加上箭头号。

实例中，第一项只有左侧图标，第二项左右均有图标，第三项有右侧图标（还有注释 item-note），第四项有badge（标记）元素。

```html
<div class="list">

  <a class="item item-icon-left" href="#">
    <i class="icon ion-email"></i>
    Check mail
  </a>

  <a class="item item-icon-left item-icon-right" href="#">
    <i class="icon ion-chatbubble-working"></i>
    Call Ma
    <i class="icon ion-ios-telephone-outline"></i>
  </a>

  <a class="item item-icon-left" href="#">
    <i class="icon ion-mic-a"></i>
    Record album
    <span class="item-note">
      Grammy
    </span>
  </a>

  <a class="item item-icon-left" href="#">
    <i class="icon ion-person-stalker"></i>
    Friends
    <span class="badge badge-assertive">0</span>
  </a>

</div>
```

尝试一下 »


## 按钮列表

使用 item-button-right 或 item-button-left 类将按钮放在列表项中。

```html
<div class="list">

  <div class="item item-button-right">
    Call Ma
    <button class="button button-positive">
      <i class="icon ion-ios-telephone"></i>
    </button>
  </div>

  ...

</div>
```

尝试一下 »


## 带头像列表

使用 item-avatar 来创建一个带头像的列表：

```html
<div class="list">

    <a class="item item-avatar" href="#">
      <img src="venkman.jpg">
      <h2>Venkman</h2>
      <p>Back off, man. I'm a scientist.</p>
    </a>

    ...

</div>
```

尝试一下 »


## 缩略图列表

item-thumbnail-left 类用于添加左侧对齐的缩略图， item-thumbnail-right 类用于添加右侧对齐的缩略图。

```html
<div class="list">

    <a class="item item-thumbnail-left" href="#">
      <img src="cover.jpg">
      <h2>Pretty Hate Machine</h2>
      <p>Nine Inch Nails</p>
    </a>

    ...

</div>
```

尝试一下 »


## 内嵌列表(inset list)

我们可以在容器当中内嵌列表，列表不会显示完整的宽度。

内嵌列表的样式为：list list-inset，与常规列表区别是，它设置了外边距（marign）,类似于选项卡。

内嵌列表是没有阴影效果的，滚动时效果会更好。

```html
<div class="list list-inset">

    <div class="item">
      Raiders of the Lost Ark
    </div>

    ...

</div>
```

尝试一下 »


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ionic 列表` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
