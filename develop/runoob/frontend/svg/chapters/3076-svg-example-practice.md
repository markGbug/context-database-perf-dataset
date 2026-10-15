# SVG：SVG 基本语法

- 来源：[SVG 基本语法](https://www.runoob.com/svg/svg-example.html)
- 分类：前端开发
- 技术：SVG
- 笔记类型：练习笔记
- 章节序号：3076

## 本章内容

SVG 文档由一个或多个 SVG 元素组成，它们定义了图形的内容和属性。

```html
<svg
  width="200"     <!-- 指定SVG画布的宽度 -->
  height="200"    <!-- 指定SVG画布的高度 -->
  xmlns="http://www.w3.org/2000/svg">   <!-- 指定SVG命名空间 -->
  <!-- SVG图形内容 -->
</svg>
```

- width 和 height 属性定义了SVG画布的宽度和高度。
- xmlns 属性指定 SVG 文档的 XML 命名空间。

SVG 的基本语法：

- SVG文档以 <svg> 标签开始，以 </svg> 标签结束。
- SVG元素使用标签来描述不同的图形，例如 <circle> 表示圆形，<rect> 表示矩形等。
- SVG元素可以包含属性，用于指定图形的各种特性，如位置、大小、颜色等。

绘制基本图形：

SVG 提供了一系列的图形元素来绘制各种形状的图形，如矩形、圆形、直线、多边形等。

- <rect>：绘制矩形
- <circle>：绘制圆形
- <ellipse>：绘制椭圆
- <line>：绘制直线
- <polyline>：绘制折线
- <polygon>：绘制多边形
- <path>：绘制路径

矩形（Rectangles）：使用 <rect> 元素绘制矩形，可以指定矩形的位置、大小、圆角等属性。


## 简单的 SVG 实例

SVG 文件推荐使用 .svg（全部小写）作为此类文件的扩展名。

1、以下是一个简单的 SVG 文件示例，创建一个包含一个圆形的 SVG 图像：


## test.svg 文件

这段代码描述了一个 SVG 画布，宽度为 200 个单位，高度也为 200 个单位。在画布上绘制了一个圆形，圆心坐标为(100, 100)，半径为80个单位，填充颜色为蓝色。

预览效果：

2、另一个简单的 SVG 图形例子：


## test.svg 文件

显示结果如下：

SVG 代码解析：

- <svg version="1.1" baseProfile="full" width="300" height="200" xmlns="http://www.w3.org/2000/svg">：这是SVG文档的开始标签，指定了SVG的版本、基本配置（full），以及画布的宽度和高度。xmlns属性定义了SVG文档的XML命名空间。
- <rect width="100%" height="100%" stroke="red" stroke-width="4" fill="yellow" />：这是一个矩形元素，使用<rect>标签表示。它的宽度和高度都设置为画布的宽度和高度（100%），stroke属性指定了矩形的边框颜色为红色，stroke-width属性设置了边框的宽度为4个单位，fill属性指定了矩形的填充颜色为黄色。
- <circle cx="150" cy="100" r="80" fill="green" />：这是一个圆形元素，使用<circle>标签表示。它的圆心坐标(cx, cy)分别为(150, 100)，半径r为80个单位，fill属性指定了圆形的填充颜色为绿色。
- <text x="150" y="115" font-size="16" text-anchor="middle" fill="white">RUNOOB SVG TEST</text>：这是一个文本元素，使用<text>标签表示。它的起始坐标(x, y)为(150, 115)，font-size属性设置了字体大小为16个单位，text-anchor属性设置了文本的水平对齐方式为居中，fill属性指定了文本的颜色为白色。文本内容为"RUNOOB SVG TEST"。
- </svg>：这是SVG文档的结束标签，标志着SVG文档的结束。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SVG 基本语法` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
