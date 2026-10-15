# Dash：Dash 数据可视化与 Plotly 集成

- 来源：[Dash Plotly](https://www.runoob.com/dash/dash-dataviews-plotly.html)
- 分类：Python / 数据科学
- 技术：Dash
- 笔记类型：学习笔记
- 章节序号：3801

## 本章内容

在数据科学和分析领域，数据可视化是一个至关重要的环节，通过可视化，我们可以更直观地理解数据，发现其中的模式和趋势。

Dash 的核心可视化功能依赖于 Plotly，这是一个强大的开源数据可视化库，Plotly 提供了丰富的图表类型和高度可定制的选项，能够轻松创建交互式图表。

Dash 通过 dcc.Graph 组件与 Plotly 无缝集成，用户可以直接在 Dash 应用中嵌入 Plotly 图表。


### 什么是 Plotly？

Plotly 是一个基于 JavaScript 的开源数据可视化库，支持多种编程语言，包括 Python、R、Julia 等。

Plotly 提供了丰富的图表类型，如折线图、柱状图、散点图、热力图等，并且支持交互功能，如缩放、平移、悬停提示等。

Plotly 特点：

- 丰富的图表类型：折线图、柱状图、散点图、饼图、热力图、3D 图等。
- 交互性：支持缩放、平移、悬停提示等交互功能。
- 高度可定制：可以自定义图表的颜色、布局、注释等。
- 与 Dash 无缝集成：通过 dcc.Graph 组件直接在 Dash 应用中嵌入 Plotly 图表。


### Plotly 的核心优势

- 交互性: Plotly 图表支持丰富的交互功能，用户可以通过鼠标操作与图表进行互动。
- 多样性: Plotly 提供了多种图表类型，适用于不同的数据可视化需求。
- 易用性: Plotly 的 API 设计简洁，易于上手，同时支持高级定制。


## Dash 与 Plotly 集成


### 1、安装 Dash 和 Plotly

在开始之前，我们需要安装 Dash 和 Plotly。可以通过以下命令进行安装：

```text
pip install dash plotly
或
pip3 install dash plotly
```

dcc.Graph 是 Dash 中用于显示 Plotly 图表的组件。它的核心参数是 figure，用于指定图表的数据和布局。

figure 参数：

- data：图表的数据部分，是一个字典列表，每个字典表示一个数据系列。
- layout：图表的布局部分，用于设置标题、坐标轴、图例等。


## 实例

显示效果如下：


### 2、创建一个简单的 Dash 应用

首先，我们创建一个简单的 Dash 应用，展示一个基本的 Plotly 图表。


## 实例

代码解析:

- 数据集创建: 我们使用 pandas 创建了一个简单的数据集 df，包含水果、数量和城市信息。
- 图表创建: 使用 plotly.express 的 px.bar 函数创建了一个柱状图，展示了不同城市中各种水果的数量。
- Dash 应用布局: 使用 html.Div 和 dcc.Graph 定义了应用的布局，其中 dcc.Graph 用于嵌入 Plotly 图表。
- 运行应用: 通过 app.run(debug=True) 启动应用，并开启调试模式。

显示效果如下：


### 3、添加交互功能

Dash 的强大之处在于其交互功能，我们可以通过 Dash 的回调机制，动态更新图表内容。


## 实例

代码解析：

- 下拉菜单: 添加了一个 dcc.Dropdown 组件，用户可以选择不同的城市。
- 回调函数: 使用 @app.callback 装饰器定义了一个回调函数 update_graph，当用户选择不同的城市时，图表会动态更新。
- 图表更新: 回调函数根据用户选择的城市过滤数据集，并更新图表。

显示效果如下：


## Plotly Express

Plotly Express 是 Plotly 的高级接口，能够用极简的代码创建复杂的图表。它非常适合快速原型开发。


### 常用图表类型

1、折线图 (px.line)：

```text
import plotly.express as px
df = px.data.iris()
fig = px.line(df, x='sepal_width', y='sepal_length', title='折线图示例')
```

2、柱状图 (px.bar)：

```text
fig = px.bar(df, x='species', y='sepal_length', title='柱状图示例')
```

3、散点图 (px.scatter)：

```text
fig = px.scatter(df, x='sepal_width', y='sepal_length', color='species', title='散点图示例')
```

4、饼图 (px.pie)：

```text
fig = px.pie(df, names='species', values='sepal_length', title='饼图示例')
```

5、热力图 (px.imshow)：

```text
import numpy as np
data = np.random.rand(10, 10)
fig = px.imshow(data, title='热力图示例')
```

以下是一个完整的 Dash 应用示例，使用 Plotly Express 创建图表：


## 实例

显示如下：


## 使用 Plotly Graph Objects

Plotly Graph Objects 是 Plotly 的低级接口，提供了更细粒度的控制，适合需要高度定制的场景。


### 常用图表类型

1、折线图 (go.Scatter)：

```text
import plotly.graph_objects as go
fig = go.Figure(data=go.Scatter(x=[1, 2, 3], y=[4, 1, 2], mode='lines'))
```

2、柱状图 (go.Bar)：

```text
fig = go.Figure(data=go.Bar(x=['A', 'B', 'C'], y=[10, 20, 30]))
```

3、散点图 (go.Scatter)：

```text
fig = go.Figure(data=go.Scatter(x=[1, 2, 3], y=[4, 1, 2], mode='markers'))
```

4、饼图 (go.Pie)：

```text
fig = go.Figure(data=go.Pie(labels=['A', 'B', 'C'], values=[10, 20, 30]))
```

以下是一个完整的 Dash 应用示例，使用 Plotly Graph Objects 创建图表：


## 实例

显示如下：


## 复习重点

- 能说明 `Dash Plotly` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
