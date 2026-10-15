# Matplotlib：Matplotlib 绘制多图

- 来源：[Matplotlib 绘制多图](https://www.runoob.com/matplotlib/matplotlib-subplots.html)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 笔记类型：练习笔记
- 章节序号：3966

## 本章内容

我们可以使用 pyplot 中的 subplot() 和 subplots() 方法来绘制多个子图。

subplot() 方法在绘图时需要指定位置，subplots() 方法可以一次生成多个，在调用时只需要调用生成对象的 ax 即可。


### subplot

```text
subplot(nrows, ncols, index, **kwargs)
subplot(pos, **kwargs)
subplot(**kwargs)
subplot(ax)
```

以上函数将整个绘图区域分成 nrows 行和 ncols 列，然后从左到右，从上到下的顺序对每个子区域进行编号 1...N ，左上的子区域的编号为 1、右下的区域编号为 N，编号可以通过参数 index 来设置。

设置 numRows ＝ 1，numCols ＝ 2，就是将图表绘制成 1x2 的图片区域, 对应的坐标为：

```text
(1, 1), (1, 2)
```

plotNum ＝ 1, 表示的坐标为(1, 1), 即第一行第一列的子图。

plotNum ＝ 2, 表示的坐标为(1, 2), 即第一行第二列的子图。

实例 import matplotlib.pyplot as plt import numpy as np #plot 1: xpoints = np.array([0, 6]) ypoints = np.array([0, 100]) plt.subplot(1, 2, 1) plt.plot(xpoints,ypoints) plt.title("plot 1") #plot 2: x = np.array([1, 2, 3, 4]) y = np.array([1, 4, 9, 16]) plt.subplot(1, 2, 2) plt.plot(x,y) plt.title("plot 2") plt.suptitle("RUNOOB subplot Test") plt.show() 显示结果如下： 设置 numRows ＝ 2，numCols ＝ 2，就是将图表绘制成 2x2 的图片区域, 对应的坐标为： (1, 1), (1, 2) (2, 1), (2, 2) plotNum ＝ 1, 表示的坐标为(1, 1), 即第一行第一列的子图。 plotNum ＝ 2, 表示的坐标为(1, 2), 即第一行第二列的子图。 plotNum ＝ 3, 表示的坐标为(2, 1), 即第二行第一列的子图。 plotNum ＝ 4, 表示的坐标为(2, 2), 即第二行第二列的子图。 实例 import matplotlib.pyplot as plt import numpy as np #plot 1: x = np.array([0, 6]) y = np.array([0, 100]) plt.subplot(2, 2, 1) plt.plot(x,y) plt.title("plot 1") #plot 2: x = np.array([1, 2, 3, 4]) y = np.array([1, 4, 9, 16]) plt.subplot(2, 2, 2) plt.plot(x,y) plt.title("plot 2") #plot 3: x = np.array([1, 2, 3, 4]) y = np.array([3, 5, 7, 9]) plt.subplot(2, 2, 3) plt.plot(x,y) plt.title("plot 3") #plot 4: x = np.array([1, 2, 3, 4]) y = np.array([4, 5, 6, 7]) plt.subplot(2, 2, 4) plt.plot(x,y) plt.title("plot 4") plt.suptitle("RUNOOB subplot Test") plt.show() 显示结果如下： subplots() subplots() 方法语法格式如下： matplotlib.pyplot.subplots(nrows=1, ncols=1, *, sharex=False, sharey=False, squeeze=True, subplot_kw=None, gridspec_kw=None, **fig_kw) 参数说明：

- nrows：默认为 1，设置图表的行数。
- ncols：默认为 1，设置图表的列数。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Matplotlib 绘制多图` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
