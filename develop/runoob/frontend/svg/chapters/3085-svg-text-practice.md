# SVG：SVG 文本 <text>

- 来源：[SVG 文本](https://www.runoob.com/svg/svg-text.html)
- 分类：前端开发
- 技术：SVG
- 笔记类型：练习笔记
- 章节序号：3085

## 本章内容

SVG 中的 <text> 元素用于在 SVG 图像中添加文本内容，它允许你在指定的位置显示文本，并可以通过设置属性来控制文本的样式、字体、大小等。


### 基本语法

```html
<text
  x="x-coordinate"          <!-- 文本左上角的 x 坐标 -->
  y="y-coordinate"          <!-- 文本左上角的 y 坐标 -->
  font-family="font"        <!-- 字体名称 -->
  font-size="size"          <!-- 字体大小 -->
  fill="fill-color"         <!-- 文本颜色 -->
  text-anchor="anchor"      <!-- 文本锚点 -->
>
  Text content              <!-- 文本内容 -->
</text>
```

属性解析：

- x 和 y 属性定义了文本左上角的坐标，即文本的起始点位置。
- font-family 属性定义了文本的字体名称，可以是系统字体或自定义字体。
- font-size 属性定义了文本的字体大小，以像素为单位。
- fill 属性定义了文本的颜色。
- text-anchor 属性定义了文本锚点，即文本相对于指定坐标的对齐方式，常用取值有 "start"（默认，左对齐）、"middle"（居中对齐）和 "end"（右对齐）。

以下代码在 SVG 图像中绘制了一段文本，文本内容为 "Hello, SVG!"，字体为 Arial，大小为 20 像素，颜色为蓝色，居中对齐，并且文本左上角的坐标为 (100, 100)。

```html
<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg">
  <text x="100" y="100" font-family="Arial" font-size="20" fill="blue" text-anchor="middle">Hello, SVG!</text>
</svg>
```


### 实例 1

写一个文本：

下面是 SVG 代码：


## 实例

点击查看：查看 SVG 文件。


## 实例 2

旋转的文字：

下面是 SVG 代码：


## 实例

点击查看：查看 SVG 文件。


### 实例 3

路径上的文字：

下面是 SVG 代码：


## 实例

点击查看：查看 SVG 文件。


### 实例 4

元素可以安排任何分小组与<tspan> 元素的数量。每个<tspan> 元素可以包含不同的格式和位置。几行文本(与 <tspan> 元素):

下面是 SVG 代码：


## 实例

点击查看：查看 SVG 文件。


## 实例 5

作为链接文本（ <a> 元素）：

下面是 SVG 代码：


## 实例

点击查看：查看 SVG 文件。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `SVG 文本` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
