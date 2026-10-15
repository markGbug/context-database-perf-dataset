# Matplotlib：Matplotlib 散点图

- 来源：[Matplotlib 散点图](https://www.runoob.com/matplotlib/matplotlib-scatter.html)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 笔记类型：练习笔记
- 章节序号：3967

## 本章内容

我们可以使用 pyplot 中的 scatter() 方法来绘制散点图。

scatter() 方法语法格式如下：

```text
matplotlib.pyplot.scatter(x, y, s=None, c=None, marker=None, cmap=None, norm=None, vmin=None, vmax=None, alpha=None, linewidths=None, *, edgecolors=None, plotnonfinite=False, data=None, **kwargs)
```

参数说明：

x，y：长度相同的数组，也就是我们即将绘制散点图的数据点，输入数据。

s：点的大小，默认 20，也可以是个数组，数组每个参数为对应点的大小。

c：点的颜色，默认蓝色 'b'，也可以是个 RGB 或 RGBA 二维行数组。

marker：点的样式，默认小圆圈 'o'。

cmap：Colormap，默认 None，标量或者是一个 colormap 的名字，只有 c 是一个浮点数数组的时才使用。如果没有申明就是 image.cmap。

norm：Normalize，默认 None，数据亮度在 0-1 之间，只有 c 是一个浮点数的数组的时才使用。

vmin，vmax：：亮度设置，在 norm 参数存在时会忽略。

alpha：：透明度设置，0-1 之间，默认 None，即不透明。

linewidths：：标记点的长度。

edgecolors：：颜色或颜色序列，默认为 'face'，可选值有 'face', 'none', None。

plotnonfinite：：布尔值，设置是否使用非限定的 c ( inf, -inf 或 nan) 绘制点。

**kwargs：：其他参数。

以下实例 scatter() 函数接收长度相同的数组参数，一个用于 x 轴的值，另一个用于 y 轴上的值：


## 实例

显示结果如下：

设置图标大小：


## 实例

显示结果如下：

自定义点的颜色：


## 实例

显示结果如下：

设置两组散点图：


## 实例

显示结果如下：

使用随机数来设置散点图：


## 实例

显示结果如下：


### 颜色条 Colormap

Matplotlib 模块提供了很多可用的颜色条。

颜色条就像一个颜色列表，其中每种颜色都有一个范围从 0 到 100 的值。

下面是一个颜色条的例子：

设置颜色条需要使用 cmap 参数，默认值为 'viridis'，之后颜色值设置为 0 到 100 的数组。


## 实例

显示结果如下：

如果要显示颜色条，需要使用 plt.colorbar() 方法：


## 实例

显示结果如下：

换个颜色条参数， cmap 设置为 afmhot_r：


## 实例

显示结果如下：

颜色条参数值可以是以下值：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Matplotlib 散点图` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
