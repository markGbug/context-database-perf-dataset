# SVG：SVG 直线 <line>

- 来源：[SVG 直线](https://www.runoob.com/svg/svg-line.html)
- 分类：前端开发
- 技术：SVG
- 笔记类型：学习笔记
- 章节序号：3081

## 本章内容

SVG 中的 <line> 元素用于绘制直线，它是 SVG 中常用的基本形状之一。

使用 <line> 元素可以创建两个点之间的直线，并可以通过设置属性来控制直线的位置、长度和样式。


### 基本语法

```html
<line
  x1="x1-coordinate"     <!-- 起点的 x 坐标 -->
  y1="y1-coordinate"     <!-- 起点的 y 坐标 -->
  x2="x2-coordinate"     <!-- 终点的 x 坐标 -->
  y2="y2-coordinate"     <!-- 终点的 y 坐标 -->
  stroke="stroke-color"  <!-- 直线的颜色 -->
  stroke-width="width"   <!-- 直线的宽度 -->
/>
```

属性解析:

- x1 和 y1 属性定义了直线的起点坐标。
- x2 和 y2 属性定义了直线的终点坐标。
- stroke 属性定义了直线的颜色。
- stroke-width 属性定义了直线的宽度。

以下代码绘制了一个黑色描边、宽度为 2 像素的直线，起点坐标为 (50, 50)，终点坐标为 (150, 150)。

```html
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg">
  <line x1="50" y1="50" x2="150" y2="150" stroke="black" stroke-width="2" />
</svg>
```


### 实例

下面是SVG代码：


## 实例

点击查看：查看 SVG 文件。

- x1 属性在 x 轴定义线条的开始
- y1 属性在 y 轴定义线条的开始
- x2 属性在 x 轴定义线条的结束
- y2 属性在 y 轴定义线条的结束


## 复习重点

- 能说明 `SVG 直线` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
