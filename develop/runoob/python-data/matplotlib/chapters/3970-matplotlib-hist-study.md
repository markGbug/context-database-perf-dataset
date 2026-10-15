# Matplotlib：Matplotlib 直方图

- 来源：[Matplotlib 直方图](https://www.runoob.com/matplotlib/matplotlib-hist.html)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 笔记类型：学习笔记
- 章节序号：3970

## 本章内容

我们可以使用 pyplot 中的 hist() 方法来绘制直方图。

hist() 方法是 Matplotlib 库中的 pyplot 子库中的一种用于绘制直方图的函数。

hist() 方法可以用于可视化数据的分布情况，例如观察数据的中心趋势、偏态和异常值等。

hist() 方法语法格式如下：

```text
matplotlib.pyplot.hist(x, bins=None, range=None, density=False, weights=None, cumulative=False, bottom=None, histtype='bar', align='mid', orientation='vertical', rwidth=None, log=False, color=None, label=None, stacked=False, **kwargs)
```

参数说明：

- x：表示要绘制直方图的数据，可以是一个一维数组或列表。
- bins：可选参数，表示直方图的箱数。默认为10。
- range：可选参数，表示直方图的值域范围，可以是一个二元组或列表。默认为None，即使用数据中的最小值和最大值。
- density：可选参数，表示是否将直方图归一化。默认为False，即直方图的高度为每个箱子内的样本数，而不是频率或概率密度。
- weights：可选参数，表示每个数据点的权重。默认为None。
- cumulative：可选参数，表示是否绘制累积分布图。默认为False。
- bottom：可选参数，表示直方图的起始高度。默认为None。
- histtype：可选参数，表示直方图的类型，可以是'bar'、'barstacked'、'step'、'stepfilled'等。默认为'bar'。
- align：可选参数，表示直方图箱子的对齐方式，可以是'left'、'mid'、'right'。默认为'mid'。
- orientation：可选参数，表示直方图的方向，可以是'vertical'、'horizontal'。默认为'vertical'。
- rwidth：可选参数，表示每个箱子的宽度。默认为None。
- log：可选参数，表示是否在y轴上使用对数刻度。默认为False。


## 实例

显示结果如下：

以下实例演示了如何使用 hist() 函数绘制多个数据组的直方图，并进行比较：


## 实例

以上实例中我们生成了三组不同的随机数据，并使用 hist() 函数绘制了它们的直方图。通过设置不同的均值和标准差，我们可以生成具有不同分布特征的随机数据。

我们设置了 bins 参数为 30，这意味着将数据范围分成 30 个等宽的区间，然后统计每个区间内数据的频数。

我们使用 label 参数设置了每个直方图的标签，以便在图例中显示。

然后使用 legend() 函数显示图例。最后，我们使用 title()、xlabel() 和 ylabel() 函数设置了图表的标题和坐标轴标签。

显示结果如下：

从上图中我们可以清晰地看出这三组数据的分布情况，其中 data1 和 data2 分布接近正态分布，而 data3 分布偏态。

这种比较直方图的方式可以帮助我们分析和比较不同数据组的分布情况。


### 结合 Pandas

以下实例我们结合 Pandas 来绘制直方图：


## 实例

显示结果如下：

除了数据框之外，您还可以使用 Pandas 中的 Series 对象绘制直方图。只需将数据框中的列替换为 Series 对象即可。


## 实例


## 复习重点

- 能说明 `Matplotlib 直方图` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
