# Matplotlib：Matplotlib 柱形图

- 来源：[Matplotlib 柱形图](https://www.runoob.com/matplotlib/matplotlib-bar.html)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 笔记类型：练习笔记
- 章节序号：3968

## 本章内容

我们可以使用 pyplot 中的 bar() 方法来绘制柱形图。

bar() 方法语法格式如下：

```text
matplotlib.pyplot.bar(x, height, width=0.8, bottom=None, *, align='center', data=None, **kwargs)
```

参数说明：

x：浮点型数组，柱形图的 x 轴数据。

height：浮点型数组，柱形图的高度。

width：浮点型数组，柱形图的宽度。

bottom：浮点型数组，底座的 y 坐标，默认 0。

align：柱形图与 x 坐标的对齐方式，'center' 以 x 位置为中心，这是默认值。 'edge'：将柱形图的左边缘与 x 位置对齐。要对齐右边缘的条形，可以传递负数的宽度值及 align='edge'。

**kwargs：：其他参数。

以下实例我们简单实用 bar() 来创建一个柱形图:


## 实例

显示结果如下：

垂直方向的柱形图可以使用 barh() 方法来设置：


## 实例

显示结果如下：

设置柱形图颜色：


## 实例

显示结果如下：

自定义各个柱形的颜色：


## 实例

显示结果如下：

设置柱形图宽度，bar() 方法使用 width 设置，barh() 方法使用 height 设置 height


## 实例

显示结果如下：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Matplotlib 柱形图` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
