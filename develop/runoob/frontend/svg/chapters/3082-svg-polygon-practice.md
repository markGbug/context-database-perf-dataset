# SVG：SVG 多边形 <polygon>

- 来源：[SVG 多边形](https://www.runoob.com/svg/svg-polygon.html)
- 分类：前端开发
- 技术：SVG
- 笔记类型：练习笔记
- 章节序号：3082

## 本章内容

SVG 中的 <polygon> 元素用于绘制多边形，它是 SVG 中常用的基本形状之一。

使用 <polygon> 元素可以创建闭合的多边形，并可以通过设置属性来控制多边形的顶点坐标、填充颜色、边框颜色等。


### 基本语法

```html
<polygon
  points="x1,y1 x2,y2 x3,y3 ..."   <!-- 多边形各个顶点的坐标 -->
  fill="fill-color"                <!-- 多边形的填充颜色 -->
  stroke="stroke-color"            <!-- 多边形的边框颜色 -->
  stroke-width="width"             <!-- 多边形的边框宽度 -->
/>
```

属性解析：

- points 属性定义了多边形各个顶点的坐标，多个顶点的坐标以空格或逗号分隔，并且每对坐标使用逗号分隔。
- fill 属性定义了多边形的填充颜色。
- stroke 属性定义了多边形的边框颜色。
- stroke-width 属性定义了多边形的边框宽度。

以下代码绘制了一个橙色填充、黑色描边、宽度为 2 像素的多边形，其顶点坐标分别为 (100, 10)、(150, 190) 和 (50, 190)，形成一个闭合的三角形。

```html
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg">
  <polygon points="100,10 150,190 50,190" fill="orange" stroke="black" stroke-width="2" />
</svg>
```


### 实例 1

<polygon> 标签用来创建含有不少于三个边的图形。

多边形是由直线组成，其形状是"封闭"的（所有的线条连接起来）。

polygon来自希腊。 "Poly" 意味 "many" ， "gon" 意味 "angle".

下面是 SVG 代码：


## 实例

```html
<svg  height="210" width="500">
  <polygon points="200,10 250,190 160,210"
  style="fill:lime;stroke:purple;stroke-width:1"/>
</svg>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SVG 多边形` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
