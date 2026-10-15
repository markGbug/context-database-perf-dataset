# Python：Python pyecharts 模块

- 来源：[Python pyecharts](https://www.runoob.com/python3/python-pyecharts.html)
- 分类：Python / 数据科学
- 技术：Python
- 笔记类型：学习笔记
- 章节序号：4151

## 本章内容

pyecharts 是一个基于 Apache ECharts 的 Python 数据可视化库，可以使用 Python 代码快速生成柱状图、折线图、饼图、散点图、地图等多种交互式图表。

ECharts 是一个基于 JavaScript 的开源数据可视化库，提供丰富的图表类型和交互功能。pyecharts 对 ECharts 进行了 Python 封装，使开发者无需直接编写复杂的 JavaScript 代码，就能创建功能丰富的数据可视化图表。

pyecharts 提供了简单、灵活的 API，支持自定义图表标题、坐标轴、图例、提示框、主题和动画等配置。

通过 pyecharts，可以先使用 Python 处理数据，再将数据转换为交互式图表。生成的图表通常保存为 HTML 文件，可以通过浏览器查看，也可以集成到 Web 应用程序或 Jupyter Notebook 中。

pyecharts 特点与功能：

- 简单易用： 提供直观的 Python API，通过少量代码即可创建图表，适合初学者快速入门。
- 丰富的图表类型： 支持折线图、柱状图、散点图、饼图、雷达图、地图、词云图以及 3D 图表等。
- 方便处理数据： 可以使用 Python 列表、字典等数据结构组织图表数据，也可以配合 Pandas 处理 DataFrame 数据。
- 交互性强： 支持鼠标悬停提示、图例切换、数据缩放、工具箱等交互功能，具体功能取决于图表类型和配置。
- 丰富的配置选项： 可以自定义标题、坐标轴、图例、提示框、标签、颜色以及图表尺寸等。
- 支持多种主题： 内置多种主题，可以快速改变图表的配色和整体视觉风格。
- 支持多种运行环境： 可以生成 HTML 文件，也可以在 Jupyter Notebook、Flask、Django 等环境中使用。


### pyecharts 安装

pyecharts 可以通过 pip 安装，建议使用 Python 3 环境。

pip 安装：

```text
pip install pyecharts
```

也可以使用以下命令安装或升级到最新版本：

```text
python -m pip install --upgrade pyecharts
```

如果系统使用 python3 命令，可以执行：

```text
python3 -m pip install --upgrade pyecharts
```

源码安装：

```text
git clone https://github.com/pyecharts/pyecharts.git
cd pyecharts
python -m pip install .
```

以上源码安装方式使用 pip 安装当前目录中的项目，通常不需要手动执行 python setup.py install。

安装成功后，可以通过以下命令查看 pyecharts 版本：

```text
python -c "import pyecharts; print(pyecharts.__version__)"
```

也可以在 Python 代码中查看版本：

```text
import pyecharts

print(pyecharts.__version__)
```

输出如下所示（以 pyecharts 2.1.0 为例）：

```text
2.1.0
```

pyecharts 2.1.0 于 2026 年 2 月发布，增加了对 ECharts 6.x 的支持。实际输出的版本号取决于安装的版本。

注意： pyecharts 主要负责生成图表所需的 HTML 和 JavaScript 配置，浏览器需要加载相关的 JavaScript 资源才能显示图表。如果 HTML 文件可以打开但图表显示为空白，应检查浏览器控制台以及相关资源是否加载成功。


### pyecharts 图表类型

pyecharts 支持多种图表类型，以下是一些常用图表及对应的 Python 类：

说明： Timeline 主要用于按照时间顺序组织和切换多个图表，并不是独立的数据图表类型。地图、地理坐标系图和部分 3D 图表可能需要加载额外的 JavaScript 或地图数据资源。


### 创建第一个图表

接下来使用 pyecharts 创建一个简单的柱状图，展示某产品在五个月份的销售额。


## 实例

以上代码首先使用 Bar() 创建柱状图对象，然后通过 add_xaxis() 添加月份数据，使用 add_yaxis() 添加销售额数据，最后调用 render() 生成图表。

如果在 bar_chart.render() 中不指定文件路径，pyecharts 默认会在当前工作目录下生成一个名为 render.html 的文件。

以上代码，执行结果为：

如果希望指定图表文件名或保存路径，可以在 render() 方法中传入文件路径参数，例如：

```text
bar_chart.render("my_bar_chart.html")
```

这样生成的图表将保存在当前工作目录下的 my_bar_chart.html 文件中。

注意： render() 默认生成的是交互式 HTML 文件，而不是 PNG、JPG 等静态图片。如果需要导出为图片，通常需要配合截图工具或其他图像导出方案。

设置图表配置选项

上面的柱状图已经能够正常显示数据，但缺少标题和坐标轴说明。我们可以使用 pyecharts 提供的配置项，为图表添加标题、横轴名称和纵轴名称。


## 实例

说明：

- Bar()：创建一个柱状图对象。
- add_xaxis()：添加横轴数据，本例为月份。
- add_yaxis()：添加数据系列，本例为各月份的销售额。
- set_global_opts()：设置图表的全局配置项。
- opts.TitleOpts()：设置图表标题。
- opts.AxisOpts()：设置坐标轴名称等属性。
- render()：将图表渲染为 HTML 文件。

生成的图表将保存为 bar_chart.html 文件，可以直接使用浏览器打开查看。


### 使用主题

pyecharts 内置了多种图表主题，可以通过主题快速调整图表的背景、颜色和整体风格。

例如，可以使用 ThemeType.LIGHT 创建亮色主题，也可以使用 ThemeType.DARK 创建深色主题。

主题需要在创建图表时，通过 opts.InitOpts() 中的 theme 参数指定，而不是通过 set_global_opts() 修改。

以下实例演示如何使用深色主题创建柱状图：


## 实例

以上代码通过 ThemeType.DARK 指定深色主题。如果希望使用亮色主题，只需要将创建图表时的参数修改为：

```text
bar_chart = Bar(
    init_opts=opts.InitOpts(theme=ThemeType.LIGHT)
)
```

说明：

- ThemeType：pyecharts 提供的主题类型常量。
- opts.InitOpts()：用于设置图表初始化选项，如主题、宽度和高度。
- theme=ThemeType.DARK：指定使用深色主题。
- theme=ThemeType.LIGHT：指定使用亮色主题。

生成的图表如下：

注意： pyecharts 的主题通常在创建图表时指定。如果需要更换主题，建议修改 InitOpts 中的参数后重新生成图表。

以下是 pyecharts 中常见的主题：

Light Themes（亮色系主题）：

- ThemeType.LIGHT：明亮主题。
- ThemeType.WHITE：简洁白色主题。
- ThemeType.WESTEROS：以蓝色为主的清新配色。
- ThemeType.ESSOS：以暖色调为主的主题。
- ThemeType.INFOGRAPHIC：信息图风格主题。
- ThemeType.MACARONS：柔和的马卡龙配色。
- ThemeType.SHINE：明亮鲜艳的配色风格。
- ThemeType.ROMA：红色、灰色等搭配的主题。
- ThemeType.VINTAGE：复古配色主题。
- ThemeType.WALDEN：以蓝绿等自然色系为主的主题。
- ThemeType.WONDERLAND：清新多彩的主题。
- ThemeType.ROMANTIC：浪漫柔和的主题。

Dark Themes（暗色系主题）：

- ThemeType.DARK：深色背景主题。
- ThemeType.CHALK：深色背景的粉笔风格主题。
- ThemeType.PURPLE_PASSION：深紫色调主题。

以上按常见视觉风格进行归类，具体的颜色和显示效果应以实际渲染结果为准。


## 设置全局配置项

set_global_opts() 是 pyecharts 中用于设置图表全局配置项的方法，可以配置标题、坐标轴、图例、提示框、工具箱等属性。

通过这些配置，可以让图表展示更多信息，并提高图表的可读性和交互性。

以下是一些常用的全局配置项：

```text
bar_chart.set_global_opts(
    title_opts=opts.TitleOpts(
        title="月度销售额柱状图",
        subtitle="副标题"
    ),
    xaxis_opts=opts.AxisOpts(name="月份"),
    yaxis_opts=opts.AxisOpts(name="销售额（万元）"),
    legend_opts=opts.LegendOpts(
        pos_left="center",
        pos_top="top"
    ),
    toolbox_opts=opts.ToolboxOpts(),
    tooltip_opts=opts.TooltipOpts(
        trigger="axis",
        axis_pointer_type="cross"
    ),
)
```

说明：

- title_opts：标题配置项，可以设置主标题、副标题及其样式。
- xaxis_opts：X 轴配置项，用于设置横轴名称、坐标轴标签和刻度等。
- yaxis_opts：Y 轴配置项，用于设置纵轴名称、坐标轴标签和刻度等。
- legend_opts：图例配置项，可以控制图例的位置、显示状态及样式。
- toolbox_opts：工具箱配置项，可以添加数据视图、保存图片等功能。
- tooltip_opts：提示框配置项，控制鼠标悬停时显示的数据和交互行为。

需要注意，部分配置选项只适用于特定图表类型，例如 xaxis_opts 和 yaxis_opts 主要用于具有坐标轴的图表。

以下实例演示如何使用多个全局配置项创建一个带有标题、图例、提示框和工具箱的柱状图：


## 实例

以上实例使用 set_global_opts() 配置了图表标题、坐标轴、图例、工具箱和提示框。

其中，toolbox_opts 可以显示图表工具箱，tooltip_opts 可以让用户在鼠标悬停时查看对应的数据。

生成的图表如下：

官方文档：https://pyecharts.org/#/zh-cn/intro

GitHub 项目：https://github.com/pyecharts/pyecharts


## 复习重点

- 能说明 `Python pyecharts` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
