# CSS3：CSS3 渐变（Gradients）

- 来源：[CSS3 渐变](https://www.runoob.com/css3/css3-gradients.html)
- 分类：前端开发
- 技术：CSS3
- 笔记类型：练习笔记
- 章节序号：2474

## 本章内容

CSS3 渐变（gradients）可以让你在两个或多个指定的颜色之间显示平稳的过渡。

以前，你必须使用图像来实现这些效果。但是，通过使用 CSS3 渐变（gradients），你可以减少下载的时间和宽带的使用。此外，渐变效果的元素在放大时看起来效果更好，因为渐变（gradient）是由浏览器生成的。

CSS3 定义了两种类型的渐变（gradients）：

- 线性渐变（Linear Gradients）- 向下/向上/向左/向右/对角方向
- 径向渐变（Radial Gradients）- 由它们的中心定义

线性渐变相关属性：background-image。

线性渐变在线工具：渐变在线工具。


## 浏览器支持

表中的数字指定了完全支持该属性的第一个浏览器版本。

注意：IE8 及更早版本的 IE 浏览器不支持该属性。


## CSS3 线性渐变

为了创建一个线性渐变，你必须至少定义两种颜色节点。颜色节点即你想要呈现平稳过渡的颜色。同时，你也可以设置一个起点和一个方向（或一个角度）。

线性渐变的实例：


### 语法

```text
background-image: linear-gradient(direction, color-stop1, color-stop2, ...);
```

线性渐变 - 从上到下（默认情况下）

下面的实例演示了从顶部开始的线性渐变。起点是红色，慢慢过渡到蓝色：


## 实例

从上到下的线性渐变：

```text
#grad {
    background-image: linear-gradient(#e66465, #9198e5);
}
```

线性渐变 - 从左到右

下面的实例演示了从左边开始的线性渐变。起点是红色，慢慢过渡到黄色：


## 实例

从左到右的线性渐变：

```text
#grad {
  height: 200px;
  background-image: linear-gradient(to right, red , yellow);
}
```

线性渐变 - 对角

你可以通过指定水平和垂直的起始位置来制作一个对角渐变。

下面的实例演示了从左上角开始（到右下角）的线性渐变。起点是红色，慢慢过渡到黄色：


## 实例

从左上角到右下角的线性渐变：

```text
#grad {
  height: 200px;
  background-image: linear-gradient(to bottom right, red, yellow);
}
```


## 使用角度

如果你想要在渐变的方向上做更多的控制，你可以定义一个角度，而不用预定义方向（to bottom、to top、to right、to left、to bottom right，等等）。


### 语法

```text
background-image: linear-gradient(angle, color-stop1, color-stop2);
```

角度是指水平线和渐变线之间的角度，逆时针方向计算。换句话说，0deg 将创建一个从下到上的渐变，90deg 将创建一个从左到右的渐变。

但是，请注意很多浏览器（Chrome、Safari、firefox等）的使用了旧的标准，即 0deg 将创建一个从左到右的渐变，90deg 将创建一个从下到上的渐变。换算公式 90 - x = y 其中 x 为标准角度，y为非标准角度。

下面的实例演示了如何在线性渐变上使用角度：


## 实例

带有指定的角度的线性渐变：

```text
#grad {
  background-image: linear-gradient(-90deg, red, yellow);
}
```


## 使用多个颜色节点

下面的实例演示了如何设置多个颜色节点：


## 实例

带有多个颜色节点的从上到下的线性渐变：

```text
#grad {
  background-image: linear-gradient(red, yellow, green);
}
```

下面的实例演示了如何创建一个带有彩虹颜色和文本的线性渐变：


## 实例

```text
#grad {
  /* 标准的语法 */
  background-image: linear-gradient(to right, red,orange,yellow,green,blue,indigo,violet);
}
```


## 使用透明度（transparent）

CSS3 渐变也支持透明度（transparent），可用于创建减弱变淡的效果。

为了添加透明度，我们使用 rgba() 函数来定义颜色节点。rgba() 函数中的最后一个参数可以是从 0 到 1 的值，它定义了颜色的透明度：0 表示完全透明，1 表示完全不透明。

下面的实例演示了从左边开始的线性渐变。起点是完全透明，慢慢过渡到完全不透明的红色：


## 实例

从左到右的线性渐变，带有透明度：

```text
#grad {
  background-image: linear-gradient(to right, rgba(255,0,0,0), rgba(255,0,0,1));
}
```


## 重复的线性渐变

repeating-linear-gradient() 函数用于重复线性渐变：


## 实例

一个重复的线性渐变：

```text
#grad {
  /* 标准的语法 */
  background-image: repeating-linear-gradient(red, yellow 10%, green 20%);
}
```


## CSS3 径向渐变

径向渐变由它的中心定义。

为了创建一个径向渐变，你也必须至少定义两种颜色节点。颜色节点即你想要呈现平稳过渡的颜色。同时，你也可以指定渐变的中心、形状（圆形或椭圆形）、大小。默认情况下，渐变的中心是 center（表示在中心点），渐变的形状是 ellipse（表示椭圆形），渐变的大小是 farthest-corner（表示到最远的角落）。

径向渐变的实例：


### 语法

```text
background-image: radial-gradient(shape size at position, start-color, ..., last-color);
```

径向渐变 - 颜色节点均匀分布（默认情况下）


## 实例

颜色节点均匀分布的径向渐变：

```text
#grad {
  background-image: radial-gradient(red, yellow, green);
}
```

径向渐变 - 颜色节点不均匀分布


## 实例

颜色节点不均匀分布的径向渐变：

```text
#grad {
  background-image: radial-gradient(red 5%, yellow 15%, green 60%);
}
```


## 设置形状

shape 参数定义了形状。它可以是值 circle 或 ellipse。其中，circle 表示圆形，ellipse 表示椭圆形。默认值是 ellipse。


## 实例

形状为圆形的径向渐变：

```text
#grad {
  background-image: radial-gradient(circle, red, yellow, green);
}
```


## 不同尺寸大小关键字的使用

size 参数定义了渐变的大小。它可以是以下四个值：

- closest-side
- farthest-side
- closest-corner
- farthest-corner


## 实例

带有不同尺寸大小关键字的径向渐变：

```text
#grad1 {
  background-image: radial-gradient(closest-side at 60% 55%, red, yellow, black);
}

#grad2 {
  background-image: radial-gradient(farthest-side at 60% 55%, red, yellow, black);
}
```


## 后续章节

- 重复的径向渐变
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS3 渐变` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
