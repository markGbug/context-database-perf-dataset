# Matplotlib：Seaborn 教程

- 来源：[Seaborn 教程](https://www.runoob.com/matplotlib/seaborn-tutorial.html)
- 分类：Python / 数据科学
- 技术：Matplotlib
- 笔记类型：学习笔记
- 章节序号：3975

## 本章内容

Seaborn 是一个建立在 Matplotlib 基础之上的 Python 数据可视化库，专注于绘制各种统计图形，以便更轻松地呈现和理解数据。

Seaborn 的设计目标是简化统计数据可视化的过程，提供高级接口和美观的默认主题，使得用户能够通过少量的代码实现复杂的图形。

Seaborn 提供了一些简单的高级接口，可以轻松地绘制各种统计图形，包括散点图、折线图、柱状图、热图等，而且具有良好的美学效果。

Seaborn 在设计时注重美观性，其默认主题和颜色调色板经过精心选择，使得绘图更加吸引人。

安装 Seaborn:

```text
pip install seaborn
```

Seaborn 提供了多种内置主题和颜色调色板，可以通过设置来改变图形的外观。


## 实例

通过设置 sns.set_theme() 函数，可以选择不同的主题和模板，以下是 Seaborn 内置的一些主题和模板：


### 主题（Theme）

darkgrid（默认）：深色网格主题。

```text
import seaborn as sns

# 设置为 darkgrid 主题
sns.set_theme(style="darkgrid")
```

whitegrid：浅色网格主题。

```text
import seaborn as sns

# 设置为 whitegrid 主题
sns.set_theme(style="whitegrid")
```

dark：深色主题，没有网格。

```text
import seaborn as sns

# 设置为 dark 主题
sns.set_theme(style="dark")
```

white：浅色主题，没有网格。

```text
import seaborn as sns

# 设置为 white 主题
sns.set_theme(style="white")
```

ticks：深色主题，带有刻度标记。

```text
import seaborn as sns

# 设置为 ticks 主题
sns.set_theme(style="ticks")
```


### 模板（Context）

paper：适用于小图，具有较小的标签和线条。

```text
import seaborn as sns

# 设置为 paper 模板
sns.set_theme(context="paper")
```

notebook（默认）：适用于笔记本电脑和类似环境，具有中等大小的标签和线条。

```text
import seaborn as sns

# 设置为 notebook 模板
sns.set_theme(context="notebook")
```

talk：适用于演讲幻灯片，具有大尺寸的标签和线条。

```text
import seaborn as sns

# 设置为 talk 模板
sns.set_theme(context="talk")
```

poster：适用于海报，具有非常大的标签和线条。

```text
import seaborn as sns

# 设置为 poster 模板
sns.set_theme(context="poster")
```

通过设置不同的主题和模板，可以调整 Seaborn 图形的大小、线条的粗细、颜色等属性，以适应不同的绘图场景。这些内置的主题和模板使得用户能够更轻松地创建美观且具有一致性的图形。

以下实例使用 Seaborn 和 Matplotlib 绘制了一个简单的柱状图，用于展示不同产品的销售情况：


## 实例

结果如下图所示：


## 绘图函数

Seaborn 提供了多个绘图函数，用于创建各种统计图形，以下是 Seaborn 主要的几个绘图函数及相应的实例：


### 1. 散点图 - sns.scatterplot()

用于绘制两个变量之间的散点图，可选择添加趋势线。


## 实例

结果如下图所示：


### 2. 折线图 - sns.lineplot()

用于绘制变量随着另一个变量变化的趋势线图。


## 实例

结果如下图所示：


### 3. 柱状图 - sns.barplot()

用于绘制变量的均值或其他聚合函数的柱状图。


## 实例

结果如下图所示：


### 4. 箱线图 - sns.boxplot()

用于绘制变量的分布情况，包括中位数、四分位数等。


## 实例

结果如下图所示：


### 5. 热图 - sns.heatmap()

用于绘制矩阵数据的热图，通常用于展示相关性矩阵。


## 实例

结果如下图所示：


### 6. 小提琴图 - sns.violinplot()

用于显示分布的形状和密度估计，结合了箱线图和核密度估计。


## 实例

结果如下图所示：

更多内容可以参考官网教程：https://seaborn.pydata.org/tutorial.html


## 复习重点

- 能说明 `Seaborn 教程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
