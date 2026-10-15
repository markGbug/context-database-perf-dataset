# Matplotlib：Matplotlib 网格线

- 来源：[Matplotlib 网格线](https://www.runoob.com/matplotlib/matplotlib-grid.html)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 笔记类型：练习笔记
- 章节序号：3965

## 本章内容

我们可以使用 pyplot 中的 grid() 方法来设置图表中的网格线。

grid() 方法语法格式如下：

```text
matplotlib.pyplot.grid(b=None, which='major', axis='both', )
```

参数说明：

- b：可选，默认为 None，可以设置布尔值，true 为显示网格线，false 为不显示，如果设置 **kwargs 参数，则值为 true。
- which：可选，可选值有 'major'、'minor' 和 'both'，默认为 'major'，表示应用更改的网格线。
- axis：可选，设置显示哪个方向的网格线，可以是取 'both'（默认），'x' 或 'y'，分别表示两个方向，x 轴方向或 y 轴方向。
- **kwargs：可选，设置网格样式，可以是 color='r', linestyle='-' 和 linewidth=2，分别表示网格线的颜色，样式和宽度。

以下实例添加一个简单的网格线，参数使用默认值：


## 实例

显示结果如下：

以下实例添加一个简单的网格线，axis 参数使用 x，设置 x 轴方向显示网格线：


## 实例

显示结果如下：

以下实例添加一个简单的网格线，并设置网格线的样式，格式如下：

```text
grid(color = 'color', linestyle = 'linestyle', linewidth = number)
```

参数说明：

color：'b' 蓝色，'m' 洋红色，'g' 绿色，'y' 黄色，'r' 红色，'k' 黑色，'w' 白色，'c' 青绿色，'#008000' RGB 颜色符串。

linestyle：'‐' 实线，'‐‐' 破折线，'‐.' 点划线，':' 虚线。

linewidth：设置线的宽度，可以设置一个数字。


## 实例

显示结果如下：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Matplotlib 网格线` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
