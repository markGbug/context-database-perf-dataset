# HTML：HTML5 Canvas

- 来源：[HTML5 Canvas](https://www.runoob.com/html/html5-canvas.html)
- 分类：前端开发
- 技术：HTML
- 笔记类型：练习笔记
- 章节序号：2634

## 本章内容

<canvas> 标签定义图形，比如图表和其他图像，您必须使用脚本来绘制图形。

在画布上（Canvas）画一个红色矩形，渐变矩形，彩色矩形，和一些彩色的文字。


## 什么是 canvas?

HTML5 <canvas> 元素用于图形的绘制，通过脚本 (通常是JavaScript)来完成.

<canvas> 标签只是图形容器，您必须使用脚本来绘制图形。

你可以通过多种方法使用 canvas 绘制路径,盒、圆、字符以及添加图像。


## 浏览器支持

表格中的数字表示支持 <canvas> 元素的第一个浏览器版本号。


## 创建一个画布（Canvas）

一个画布在网页中是一个矩形框，通过 <canvas> 元素来绘制.

注意: 默认情况下 <canvas> 元素没有边框和内容。

<canvas>简单实例如下:

注意: 标签通常需要指定一个id属性 (脚本中经常引用), width 和 height 属性定义的画布的大小.

提示:你可以在HTML页面中使用多个 <canvas> 元素.

使用 style 属性来添加边框:


## 实例

```html
<canvas id="myCanvas" width="200" height="100"
style="border:1px solid #000000;">
</canvas>
```


## 使用 JavaScript 来绘制图像


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `HTML5 Canvas` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
