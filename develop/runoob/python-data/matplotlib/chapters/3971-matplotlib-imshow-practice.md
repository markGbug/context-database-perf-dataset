# Matplotlib：Matplotlib imshow() 方法

- 来源：[Matplotlib imshow()](https://www.runoob.com/matplotlib/matplotlib-imshow.html)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 笔记类型：练习笔记
- 章节序号：3971

## 本章内容

imshow() 函数是 Matplotlib 库中的一个函数，用于显示图像。

imshow() 函数常用于绘制二维的灰度图像或彩色图像。

imshow() 函数可用于绘制矩阵、热力图、地图等。

imshow() 方法语法格式如下：

```text
imshow(X, cmap=None, norm=None, aspect=None, interpolation=None, alpha=None, vmin=None, vmax=None, origin=None, extent=None, shape=None, filternorm=1, filterrad=4.0, imlim=None, resample=None, url=None, *, data=None, **kwargs)
```

参数说明：

- X：输入数据。可以是二维数组、三维数组、PIL图像对象、matplotlib路径对象等。
- cmap：颜色映射。用于控制图像中不同数值所对应的颜色。可以选择内置的颜色映射，如gray、hot、jet等，也可以自定义颜色映射。
- norm：用于控制数值的归一化方式。可以选择Normalize、LogNorm等归一化方法。
- aspect：控制图像纵横比（aspect ratio）。可以设置为auto或一个数字。
- interpolation：插值方法。用于控制图像的平滑程度和细节程度。可以选择nearest、bilinear、bicubic等插值方法。
- alpha：图像透明度。取值范围为0~1。
- origin：坐标轴原点的位置。可以设置为upper或lower。
- extent：控制显示的数据范围。可以设置为[xmin, xmax, ymin, ymax]。
- vmin、vmax：控制颜色映射的值域范围。
- filternorm 和 filterrad：用于图像滤波的对象。可以设置为None、antigrain、freetype等。
- imlim： 用于指定图像显示范围。
- resample：用于指定图像重采样方式。


### 显示灰度图像


## 实例

以上实例中我们生成了一个 10x10 的随机数组，并使用 imshow() 函数将其显示为一张灰度图像。

我们设置了 cmap 参数为 gray，这意味着将使用灰度颜色映射显示图像。

显示结果如下：


### 显示彩色图像


## 实例

以上实例中我们生成了一个 10x10 的随机彩色图像，并使用 imshow() 函数将其显示出来。

由于彩色图像是三维数组，因此不需要设置 cmap 参数。

显示结果如下：


### 显示热力图


## 实例

以上实例中我们生成了一个 10x10 的随机数组，并使用 imshow() 函数将其显示为热力图。

我们设置了 cmap 参数为 hot，这意味着将使用热度颜色映射显示图像。

此外，我们还添加了一个颜色条（colorbar），以便查看数据的值与颜色之间的关系。

显示结果如下：


### 显示地图


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Matplotlib imshow()` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
