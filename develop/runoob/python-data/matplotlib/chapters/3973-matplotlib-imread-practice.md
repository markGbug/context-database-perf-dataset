# Matplotlib：Matplotlib imread() 方法

- 来源：[Matplotlib imread()](https://www.runoob.com/matplotlib/matplotlib-imread.html)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 笔记类型：练习笔记
- 章节序号：3973

## 本章内容

imread() 方法是 Matplotlib 库中的一个函数，用于从图像文件中读取图像数据。

imread() 方法返回一个 numpy.ndarray 对象，其形状是 (nrows, ncols, nchannels)，表示读取的图像的行数、列数和通道数：

- 如果图像是灰度图像，则 nchannels 为 1。
- 如果是彩色图像，则 nchannels 为 3 或 4，分别表示红、绿、蓝三个颜色通道和一个 alpha 通道。

imread() 方法的语法如下：

```text
matplotlib.pyplot.imread(fname, format=None)
```

参数说明：

- fname：指定了要读取的图像文件的文件名或文件路径，可以是相对路径或绝对路径。
- format ：参数指定了图像文件的格式，如果不指定，则默认根据文件后缀名来自动识别格式。

以下实例演示了如何使用 imread 函数从一张图像文件中读取图像数据，并将其显示出来：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Matplotlib imread()` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
