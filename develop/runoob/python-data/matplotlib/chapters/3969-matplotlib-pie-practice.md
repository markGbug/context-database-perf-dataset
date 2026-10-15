# Matplotlib：Matplotlib 饼图

- 来源：[Matplotlib 饼图](https://www.runoob.com/matplotlib/matplotlib-pie.html)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 笔记类型：练习笔记
- 章节序号：3969

## 本章内容

饼图（Pie Chart）是一种常用的数据可视化图形，用来展示各类别在总体中所占的比例。

我们可以使用 pyplot 中的 pie() 方法来绘制饼图。

pie() 方法语法格式如下：

```text
matplotlib.pyplot.pie(x, explode=None, labels=None, colors=None, autopct=None, pctdistance=0.6, shadow=False, labeldistance=1.1, startangle=0, radius=1, counterclock=True, wedgeprops=None, textprops=None, center=0, 0, frame=False, rotatelabels=False, *, normalize=None, data=None)[source]
```

参数说明：

- x：浮点型数组或列表，用于绘制饼图的数据，表示每个扇形的面积。
- explode：数组，表示各个扇形之间的间隔，默认值为0。
- labels：列表，各个扇形的标签，默认值为 None。
- colors：数组，表示各个扇形的颜色，默认值为 None。
- autopct：设置饼图内各个扇形百分比显示格式，%d%% 整数百分比，%0.1f 一位小数， %0.1f%% 一位小数百分比， %0.2f%% 两位小数百分比。
- labeldistance：标签标记的绘制位置，相对于半径的比例，默认值为 1.1，如 <1则绘制在饼图内侧。
- pctdistance：：类似于 labeldistance，指定 autopct 的位置刻度，默认值为 0.6。
- shadow：：布尔值 True 或 False，设置饼图的阴影，默认为 False，不设置阴影。
- radius：：设置饼图的半径，默认为 1。
- startangle：：用于指定饼图的起始角度，默认为从 x 轴正方向逆时针画起，如设定 =90 则从 y 轴正方向画起。
- counterclock：布尔值，用于指定是否逆时针绘制扇形，默认为 True，即逆时针绘制，False 为顺时针。
- wedgeprops ：字典类型，默认值 None。用于指定扇形的属性，比如边框线颜色、边框线宽度等。例如：wedgeprops={'linewidth':5} 设置 wedge 线宽为5。
- textprops ：字典类型，用于指定文本标签的属性，比如字体大小、字体颜色等，默认值为 None。


## 实例

显示结果如下：

设置饼图各个扇形的标签与颜色：


## 实例

显示结果如下：

突出显示第二个扇形，并格式化输出百分比：


## 实例

我们定义了一个包含 4 个元素的列表 sizes，它表示各个类别在总体中所占的比例。然后，我们定义了一个包含 4 个元素的列表 labels，它表示各个类别的标签。接下来，我们定义了一个包含 4 个元素的列表 colors，它表示每个类别的颜色。然后，我们定义了一个包含 4 个元素的元组 explode，它用来指定是否突出某个扇形。接着，我们调用 plt.pie 函数来绘制饼图，其中传入了上述参数。最后，我们添加了一个标题，并调用 plt.show() 来显示图形。

显示结果如下：


## 实例

注意：默认情况下，第一个扇形的绘制是从 x 轴开始并逆时针移动：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Matplotlib 饼图` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
