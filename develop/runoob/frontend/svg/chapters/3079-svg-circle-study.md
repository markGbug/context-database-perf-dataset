# SVG：SVG 圆形 <circle>

- 来源：[SVG 圆形](https://www.runoob.com/svg/svg-circle.html)
- 分类：前端开发
- 技术：SVG
- 笔记类型：学习笔记
- 章节序号：3079

## 本章内容

SVG 中的 <circle> 元素用于绘制圆形，它是SVG中常用的基本形状之一。

使用 <circle> 元素可以创建圆形的图形，并可以通过设置属性来控制圆形的位置、大小和样式。


### 基本语法

```html
<circle
  cx="x-coordinate"      <!-- 圆心的 x 坐标 -->
  cy="y-coordinate"      <!-- 圆心的 y 坐标 -->
  r="radius"             <!-- 圆的半径 -->
  fill="fill-color"      <!-- 圆的填充颜色 -->
  stroke="stroke-color"  <!-- 圆的描边颜色 -->
  stroke-width="width"   <!-- 圆的描边宽度 -->
/>
```

属性解析：

- cx 和 cy 属性定义了圆心的坐标，即圆的中心点的位置。
- r 属性定义了圆的半径，以确定圆的大小。
- fill 属性定义了圆的填充颜色。
- stroke 属性定义了圆的描边颜色。
- stroke-width 属性定义了圆的描边宽度。

以下代码绘制了一个蓝色填充、黑色描边、半径为 50 像素的圆形，圆心坐标为 (100, 100)。

```html
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg">
  <circle cx="100" cy="100" r="50" fill="blue" stroke="black" stroke-width="2" />
</svg>
```


### 实例

下面是 SVG 代码：


## 实例

点击查看：查看 SVG 文件。

代码解析：

- cx 和 cy 属性定义圆点的 x 和 y 坐标。如果省略 cx 和 cy，圆的中心会被设置为 (0, 0)
- r 属性定义圆的半径


## 复习重点

- 能说明 `SVG 圆形` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
