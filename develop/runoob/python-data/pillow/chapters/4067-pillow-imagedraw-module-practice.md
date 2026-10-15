# Pillow：Pillow ImageDraw 模块

- 来源：[Pillow ImageDraw 模块](https://www.runoob.com/pillow/pillow-imagedraw-module.html)
- 分类：Python / 数据科学
- 技术：Pillow
- 笔记类型：练习笔记
- 章节序号：4067

## 本章内容

ImageDraw 是 Python 图像处理库 Pillow（PIL 的分支）中的一个模块，用于在图像上绘制各种图形和文本。

ImageDraw 提供了丰富的绘图功能，包括线条、矩形、圆形、多边形、文本等，适用于图像标注、生成图表或简单的图形设计。

ImageDraw 模块的主要特点包括：

- 支持在现有图像上绘制
- 可以创建全新的空白画布
- 提供多种绘图原语（点、线、矩形、椭圆等）
- 支持文本绘制和字体设置
- 允许自定义绘图颜色和样式


## ImageDraw 的基本使用


### 创建 Draw 对象

在使用 ImageDraw 之前，需要先创建一个 ImageDraw.Draw 对象，传入一个 Image 对象作为绘图的基础。


## 实例


### 绘制基本图形

ImageDraw 支持多种绘图方法，例如：

- 绘制线条：line()
- 绘制矩形：rectangle()
- 绘制圆形/椭圆：ellipse()
- 绘制多边形：polygon()
- 绘制文本：text()


## ImageDraw 常用方法


## 综合示例

以下是一个完整的示例，展示如何使用 ImageDraw 绘制多种图形和文本：


## 实例

运行后，会生成一个包含多种图形的图像文件 draw_example.png。


## 总结

ImageDraw 是 Pillow 中非常实用的绘图模块，适用于：

- 图像标注（如添加文字、箭头）
- 生成简单的图表或示意图
- 自定义图形绘制

通过掌握 line()、rectangle()、ellipse()、text() 等方法，可以轻松实现各种绘图需求。

如果你需要更高级的绘图功能，可以结合 ImageFont（字体设置）或 ImageFilter（滤镜效果）进一步扩展功能。

希望本教程能帮助你快速上手 Pillow 的 ImageDraw 模块！


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Pillow ImageDraw 模块` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
