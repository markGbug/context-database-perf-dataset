# Pillow：Pillow ImageTk 模块

- 来源：[Pillow ImageTk 模块](https://www.runoob.com/pillow/pillow-imagetk-module.html)
- 分类：Python / 数据科学
- 技术：Pillow
- 笔记类型：学习笔记
- 章节序号：4081

## 本章内容

ImageTk 是 Python 图像处理库 Pillow（PIL 的分支）中的一个子模块，主要用于在 Tkinter GUI 程序中显示和处理图像。

ImageTk 提供了 PhotoImage 类的替代方案，支持更多图像格式（如 JPEG、PNG），并允许直接操作图像数据。

导入方法：

```text
from PIL import Image, ImageTk
```


## ImageTk 核心方法

下表列出了 ImageTk 模块的主要方法及其功能说明：


## 基础用法示例


### 显示图片


## 实例


### 动态更新图片


## 实例


## 注意事项

- 内存管理：Tkinter 的 PhotoImage 对象需要被长期引用（如绑定到全局变量或控件属性），否则会被垃圾回收导致图像消失。
- 线程安全：Tkinter 和 ImageTk 的操作必须在主线程执行。
- 格式支持：ImageTk.PhotoImage 支持 Pillow 能解码的所有格式（如 PNG、JPEG），但 BitmapImage 仅支持 .xbm 位图。


## 常见问题


### 图片不显示

- 原因：未正确保留 PhotoImage 对象的引用。
- 解决：将 photo 绑定到控件或全局变量： label.image = photo # 关键！


### 性能优化

- 对大图像使用 thumbnail() 或 resize() 提前缩放： image.thumbnail((800, 600)) # 限制最大尺寸


## 复习重点

- 能说明 `Pillow ImageTk 模块` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
