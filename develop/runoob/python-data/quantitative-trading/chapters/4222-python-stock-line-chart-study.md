# 量化交易：Python 量化股票 K 线图

- 来源：[Python 量化股票 K 线图](https://www.runoob.com/python-qt/python-stock-line-chart.html)
- 分类：Python / 数据科学
- 技术：量化交易
- 笔记类型：学习笔记
- 章节序号：4222

## 本章内容

我们可以通过 Python pyecharts 模块来绘制股票 K 线图。

pyecharts 是一个基于 ECharts 的 Python 数据可视化库，它允许用户使用 Python 语言生成各种类型的交互式图表和数据可视化。

Python pyecharts 模块内容查看：Python pyecharts 模块。

在 pyecharts 中，可以使用 K 线图（Kline）来展示股票走势，K 线图主要用于展示金融数据，如股票的开盘价、收盘价、最高价、最低价等信息。

首先，确保你已经安装了 pyecharts：

```text
pip install pyecharts
```

我们使用雅虎财经（Yahoo Finance）的数据获取近一年的股票数据，我们可以使用 yfinance 库：

```text
pip install yfinance
```


### K 线图使用

导入相关模块：

```text
from pyecharts import options as opts
from pyecharts.charts import Kline
```

准备数据：

Kline 图的数据通常是一个包含开盘价、收盘价、最高价、最低价的二维数组，例如：

```text
data = [
    [2320.26, 2320.26, 2287.3, 2362.94],
    [2300, 2291.3, 2288.26, 2308.38],
    # ...
]
```

配置 Kline 图：

```text
kline = (
    Kline()
    .add_xaxis(xaxis_data=["2017-10-24", "2017-10-25", "2017-10-26", "2017-10-27"])
    .add_yaxis(series_name="Kline", y_axis=data)
    .set_global_opts(
        xaxis_opts=opts.AxisOpts(is_scale=True),
        yaxis_opts=opts.AxisOpts(is_scale=True),
        title_opts=opts.TitleOpts(title="Kline 示例"),
    )
)
```

在这里，使用了 add_xaxis 设置 x 轴的数据，使用 add_yaxis 添加 Kline 数据系列，set_global_opts 则用于设置全局配置，包括标题等。

渲染图表：

```text
kline.render("kline_chart.html")
```

将 Kline 图渲染到 HTML 文件中。


## 实例

说明：

- 我们有一个名为 data 的数据集，其中包含每天的金融数据，包括开盘价、收盘价、最高价和最低价。
- 我们创建了一个 Kline 实例，使用 add_xaxis 设置 x 轴数据（在这种情况下是日期），使用 add_yaxis 添加 Kline 数据系列。
- 使用 set_global_opts 设置全局选项，例如 x 轴和 y 轴的缩放，以及图表标题。
- 最后，我们使用 render 将图表渲染到一个 HTML 文件中。

当前目录会生成一个 kline_chart.html 文件，打开该文件图表显示如下：

下面是一个实例代码，演示如何获取贵州茅台的股票数据并生成 K 线图：


## 实例

当前目录会生成一个 maotai_kline_chart.html 文件，打开该文件图表显示如下：


### 绘制曲线图

我们也可以使用 pyecharts 绘制股票的简单曲线图，以茅台（600519.SH）为例：


## 实例

当前目录会生成一个 maotai_stock_trend_chart.html 文件，打开该文件图表显示如下：

可以考虑添加一些图表的工具，例如数据缩放、数据视图等，以提升用户的交互体验。

以下是优化后的代码，添加了数据缩放和数据视图的功能：


## 实例

当前目录会生成一个 maotai_stock_trend_chart2.html 文件，打开该文件图表显示如下：


## 复习重点

- 能说明 `Python 量化股票 K 线图` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
