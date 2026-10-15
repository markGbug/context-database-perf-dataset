# CSS：CSS 边框

- 来源：[CSS Border(边框)](https://www.runoob.com/css/css-border.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2402

## 本章内容

CSS 边框（Border）是用于定义元素边框样式的属性。

边框可以应用于任何 HTML 元素，用于增强视觉效果、分隔内容或突出显示元素。

CSS 边框属性主要包括边框宽度、边框样式、边框颜色以及简写属性。


## CSS 边框属性

CSS边框属性允许你指定一个元素边框的样式和颜色。

在四边都有边框

红色底部边框

圆角边框

左侧边框带宽度，颜色为蓝色


## 边框样式

边框样式属性指定要显示什么样的边界。

border-style 属性用于指定要显示的边框类型。

允许的值如下：

- dotted：定义点状边框。
- dashed：定义虚线边框。
- solid：定义实线边框。
- double：定义双线边框。
- groove：定义三维沟槽边框。效果取决于 border-color 的值。
- ridge：定义三维脊状边框。效果取决于 border-color 的值。
- inset：定义三维嵌入边框。效果取决于 border-color 的值。
- outset：定义三维突出边框。效果取决于 border-color 的值。
- none：定义无边框。
- hidden：定义隐藏边框。


### border-style 演示:

none: 默认无边框

dotted: 定义一个点线边框

dashed: 定义一个虚线边框

solid: 定义实线边框

double: 定义两个边框。 两个边框的宽度和 border-width 的值相同

groove: 定义3D沟槽边框。效果取决于边框的颜色值

ridge: 定义3D脊边框。效果取决于边框的颜色值

inset:定义一个3D的嵌入边框。效果取决于边框的颜色值

outset: 定义一个3D突出边框。 效果取决于边框的颜色值

尝试一下 »


## 边框宽度

您可以通过 border-width 属性为边框指定宽度。

为边框指定宽度有两种方法：可以指定长度值，比如 2px 或 0.1em(单位为 px, pt, cm, em 等)，或者使用 3 个关键字之一，它们分别是 thick 、medium（默认值） 和 thin。

注意：CSS 没有定义 3 个关键字的具体宽度，所以一个用户可能把 thick 、medium 和 thin 分别设置为等于 5px、3px 和 2px，而另一个用户则分别设置为 3px、2px 和 1px。


## 实例

```text
p.one
{
    border-style:solid;
    border-width:5px;
}
p.two
{
    border-style:solid;
    border-width:medium;
}
```


## 边框颜色

border-color属性用于设置边框的颜色。可以设置的颜色：

- name - 指定颜色的名称，如 "red"
- RGB - 指定 RGB 值, 如 "rgb(255,0,0)"
- Hex - 指定16进制值, 如 "#ff0000"

您还可以设置边框的颜色为"transparent"。

注意： border-color单独使用是不起作用的，必须得先使用border-style来设置边框样式。


## 实例

```text
p.one
{
    border-style:solid;
    border-color:red;
}
p.two
{
    border-style:solid;
    border-color:#98bf21;
}
```


## 边框-单独设置各边

在CSS中，可以指定不同的侧面不同的边框：


## 实例

```text
p
{
    border-top-style:dotted;
    border-right-style:solid;
    border-bottom-style:dotted;
    border-left-style:solid;
}
```

上面的例子也可以设置一个单一属性：


## 实例

```text
border-style:dotted solid;
```

border-style属性可以有1-4个值：

- border-style:dotted solid double dashed; 上边框是 dotted 右边框是 solid 底边框是 double 左边框是 dashed
- border-style:dotted solid double; 上边框是 dotted 左、右边框是 solid 底边框是 double
- border-style:dotted solid; 上、底边框是 dotted 右、左边框是 solid
- border-style:dotted;四面边框是 dotted

上面的例子用了border-style。然而，它也可以和border-width 、 border-color一起使用。


## 边框-简写属性

上面的例子用了很多属性来设置边框。

你也可以在一个属性中设置边框。

你可以在"border"属性中设置：

- border-width
- border-style (required)
- border-color


## 实例

```text
border:5px solid red;
```


## 更多实例

所有边框属性在一个声明之中 本例演示用简写属性来将所有四个边框属性设置于同一声明中。

设置下边框的样式 本例演示如何设置下边框的样式。

设置左边框的宽度 本例演示如何设置左边框的宽度。

设置四个边框的颜色 本例演示如何设置四个边框的颜色。可以设置一到四个颜色。

设置右边框的颜色 本例演示如何设置右边框的颜色。

设置渐变色边框 本例演示如何设置渐变色边框。


## CSS 边框属性


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS Border(边框)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
