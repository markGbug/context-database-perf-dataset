# Pillow：Pillow 简介

- 来源：[Pillow 简介](https://www.runoob.com/pillow/pillow-intro.html)
- 分类：Python / 数据科学
- 技术：Pillow
- 笔记类型：学习笔记
- 章节序号：4059

## 本章内容

Pillow 是 Python 编程语言中的一个强大图像处理库，它是 Python Imaging Library (PIL) 的一个友好分支（fork）。

Pillow 为 Python 提供了广泛的图像处理功能，使开发者能够轻松地打开、操作和保存多种格式的图像文件。

Pillow 提供了广泛的图像处理功能，包括但不限于：

- 图像编辑和处理：调整大小、裁剪、旋转、翻转等基本操作
- 图像增强：调整亮度、对比度、锐化、模糊等
- 网站和应用开发：处理用户上传的图像，生成缩略图等
- 计算机视觉：作为图像预处理工具
- 批量图像处理：自动化处理大量图像文件
- 图像格式转换：在不同图像格式之间转换
- 图像分析：提取图像统计数据和信息
- 水印和图像合成：添加文本、logo或合并多个图像
- 数据可视化：生成图表和视觉表示
- 艺术创作和滤镜效果：应用各种视觉效果

Pillow 因其简单易用的 API 和强大的功能，成为 Python 生态系统中处理图像任务的首选库之一。


## Pillow 的核心特点


### 1. 多种图像格式支持

Pillow 支持多种常见和专业的图像格式：

- 常见格式：JPEG, PNG, GIF, BMP, TIFF
- 特殊格式：PPM, WEBP, PCX, ICO, PSD
- 科学和专业格式：FITS, HDR, SGI


### 2. 全面的图像处理功能

- 几何变换：调整大小、裁剪、旋转、翻转、变形等
- 颜色操作：转换模式（如 RGB、CMYK、灰度等）、颜色平衡调整
- 滤镜和效果：模糊、锐化、边缘增强、轮廓检测等
- 像素级访问和修改：直接操作图像的像素数据
- 通道操作：分离和合并颜色通道


### 3. 图像增强功能

- 亮度调整
- 对比度调整
- 锐度调整
- 色彩平衡
- 饱和度调整


### 4. 图像绘制功能

通过 ImageDraw 模块提供绘图功能：

- 绘制线条、矩形、椭圆、多边形等形状
- 绘制文本，支持不同字体和字号
- 创建空白画布并进行绘制


### 5. 与其他库的集成

Pillow 可以与其他 Python 库无缝协作：

- 与 NumPy 集成，支持数组操作
- 与 Matplotlib 配合用于数据可视化
- 可以作为 OpenCV 和其他计算机视觉库的补充


### 6. 跨平台兼容性

- 支持 Windows、macOS、Linux 等主要操作系统
- 适配多种 Python 版本


### 7. 优化的性能

- C 加速的核心功能，提供高效处理
- 内存优化，适合处理大型图像文件


## Pillow 与原始 PIL 的比较


### Pillow 与 PIL 的关系

- PIL (Python Imaging Library) 是 Python 最早的图像处理库，但已停止更新（最后版本 1.1.7）。
- Pillow 是 PIL 的一个 兼容分支，修复了 PIL 的许多问题，并增加了对新 Python 版本的支持。
- Pillow 的 API 与 PIL 几乎相同，所以大多数 PIL 代码可以直接在 Pillow 上运行。
- 安装 Pillow 后，仍然使用 import PIL 或 from PIL import ... 来导入模块。


## Pillow 的主要模块

- Image: 核心模块，提供图像类和基本操作
- ImageChops: 进行通道操作和图像合成
- ImageColor: 颜色处理和转换
- ImageDraw: 在图像上绘制图形和文本
- ImageEnhance: 图像增强操作
- ImageFile: 处理图像文件
- ImageFilter: 提供预定义的图像滤镜
- ImageFont: 加载和渲染字体
- ImageGrab: 屏幕抓取功能（仅限 Windows 和 macOS）
- ImageMath: 像素级数学运算
- ImageMorph: 形态学操作
- ImageOps: 提供常用图像处理操作
- ImagePalette: 处理调色板图像
- ImagePath: 矢量图形功能
- ImageQt: 与 PyQt/PySide 的集成
- ImageSequence: 处理图像序列，如 GIF 动画
- ImageStat: 统计图像数据
- ImageTk: 与 Tkinter GUI 的集成
- ImageWin: 与 Windows 系统的集成


## Pillow 的优势和局限性


### 优势

- 易于使用：API 设计直观，易于上手
- 功能全面：满足大多数图像处理需求
- 文档完善：提供详细的文档和示例
- 活跃的社区：持续维护和更新
- 兼容性好：支持多种平台和 Python 版本
- 轻量级：相比专业图像处理软件，资源占用少


### 局限性

- 性能：对于大规模图像处理任务，可能不如专用的 C++/C 库快速
- 高级功能：某些高级图像处理功能相对有限，需结合其他库（如 OpenCV）使用
- 视频处理：不提供视频处理功能
- 3D 图像：不支持 3D 图像处理
- 机器学习集成：没有内置的机器学习功能，需要与其他库（如 TensorFlow、PyTorch）集成


## Pillow 的发展


### Pillow 历史

- 1995年：Fredrik Lundh 开始开发原始的 Python Imaging Library (PIL)
- 2009年：原始 PIL 库的最后一个版本 1.1.7 发布，之后停止更新
- 2010年：由于原始 PIL 开发停滞，社区开始寻找替代方案
- 2011年：Alex Clark 和其他贡献者创建了 Pillow 作为 PIL 的一个分支，以继续维护和开发
- 2012年：Pillow 1.0 发布
- 2014年：Pillow 2.0 发布，停止支持 Python 2.5
- 2015年：原始 PIL 的创建者 Fredrik Lundh 正式支持 Pillow 作为 PIL 的继任者
- 2016年：Pillow 3.0 发布，增加了对 Python 3.5 的支持
- 2020年：Pillow 7.0 发布，放弃对 Python 2.7 的支持
- 2021年：Pillow 8.0 发布，增强了安全性和性能
- 2022-2023年：Pillow 9.0 和 10.0 相继发布，增加了更多特性和优化


### Pillow 的未来发展

- 性能优化：持续改进处理速度和内存使用
- 新格式支持：增加对新图像格式的支持
- 安全增强：加强对恶意图像的防护
- API 改进：简化和改进 API 设计
- 与新兴技术集成：更好地支持机器学习和 AI 应用场景


## 复习重点

- 能说明 `Pillow 简介` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
