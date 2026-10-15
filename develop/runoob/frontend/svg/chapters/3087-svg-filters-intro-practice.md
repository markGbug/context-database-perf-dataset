# SVG：SVG 滤镜

- 来源：[SVG 滤镜](https://www.runoob.com/svg/svg-filters-intro.html)
- 分类：前端开发
- 技术：SVG
- 笔记类型：练习笔记
- 章节序号：3087

## 本章内容

SVG 滤镜是一种强大的图形效果技术，可以用来实现各种视觉效果，例如模糊、阴影、光照等。

滤镜可以应用于 SVG 图形元素，例如矩形、圆形、路径等，以及 SVG 文本元素，使它们呈现出不同的外观和效果。


### 基本语法

SVG 滤镜通常使用 <filter> 元素定义，并通过 filter 属性将其应用于目标元素。

```html
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg">
  <!-- 定义滤镜 -->
  <filter id="filter_id">
    <!-- 滤镜效果 -->
  </filter>

  <!-- 应用滤镜的目标元素 -->
  <rect x="50" y="50" width="100" height="80" filter="url(#filter_id)" />
</svg>
```


### 滤镜效果

SVG 滤镜可以实现多种效果，常见的滤镜效果包括：

- 模糊（Blur）：使图像产生模糊效果，通过 <feGaussianBlur> 元素实现。
- 阴影（Shadow）：为图像添加阴影效果，通过 <feDropShadow> 元素实现。
- 亮度、对比度调整（Brightness, Contrast）：调整图像的亮度和对比度，通过 <feComponentTransfer> 元素实现。
- 颜色矩阵（Color Matrix）：通过颜色矩阵操作修改图像的颜色，通过 <feColorMatrix> 元素实现。
- 混合模式（Blend Mode）：将两个图像混合在一起，通过 <feBlend> 元素实现。

以下代码定义了一个模糊滤镜，然后将其应用于一个红色填充的矩形，使矩形呈现出模糊的效果。


## 实例

SVG 可用的滤镜是：

- feBlend - 与图像相结合的滤镜
- feColorMatrix - 用于彩色滤光片转换
- feComponentTransfer
- feComposite
- feConvolveMatrix
- feDiffuseLighting
- feDisplacementMap
- feFlood
- feGaussianBlur
- feImage
- feMerge
- feMorphology
- feOffset - 过滤阴影
- feSpecularLighting
- feTile
- feTurbulence
- feDistantLight - 用于照明过滤
- fePointLight - 用于照明过滤
- feSpotLight - 用于照明过滤

除此之外，您可以在每个 SVG 元素上使用多个滤镜！


### 注意事项

- SVG 滤镜可以组合使用，可以在一个 <filter> 元素中定义多个滤镜效果。
- 每种滤镜效果都有不同的参数可以调整，例如模糊滤镜的标准差参数、阴影滤镜的偏移量和模糊半径等。
- SVG 滤镜可以与 CSS 样式表一起使用，也可以直接在SVG元素上使用 style 属性进行定义。

通过使用 SVG 滤镜，你可以为 SVG 图形元素添加各种视觉效果，使其呈现出更加生动、多样化的外观。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SVG 滤镜` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
