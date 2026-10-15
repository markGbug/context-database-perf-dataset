# Dash：Dash 常用交互组件

- 来源：[Dash 常用交互组件](https://www.runoob.com/dash/dash-dcc-component.html)
- 分类：Python / 数据科学
- 技术：Dash
- 笔记类型：学习笔记
- 章节序号：3799

## 本章内容

Dash 基于 Python，允许开发者使用纯 Python 代码构建交互式的 Web 应用。

Dash 的核心组件之一是 dash.dcc（Dash Core Components），它提供了丰富的 UI 组件，如滑块、下拉菜单、图形等，这些组件可以帮助开发者快速构建功能强大的 Web 应用。

dash.dcc 组件包括但不限于：

- Graph：用于绘制各种图表，如折线图、柱状图、散点图等。
- Dropdown：下拉菜单，允许用户从多个选项中选择一个。
- Slider：滑块，允许用户通过拖动滑块选择一个数值范围。
- Input：输入框，允许用户输入文本或数字。
- Textarea：多行文本输入框，适用于输入较长的文本内容。
- Checklist：复选框列表，允许用户选择多个选项。
- RadioItems：单选按钮列表，允许用户从多个选项中选择一个。
- DatePickerSingle 和 DatePickerRange：日期选择器，允许用户选择单个日期或日期范围。
- Upload：文件上传组件，允许用户上传文件。

这些组件是构建交互式 Web 应用的基础，开发者可以通过组合这些组件来创建复杂的用户界面。

在最新版本的 Dash 中，推荐使用以下方式导入 dcc：

```text
from dash import dcc
```


### 常用交互组件


## 应用实例


### 创建一个简单的 Dash 应用

以下是一个简单的 Dash 应用示例，展示了如何使用 dash.dcc 组件：


## 实例

以上实例中，我们创建了一个简单的 Dash 应用，包含一个输入框和一个显示输入内容的区域。

当用户在输入框中输入内容时，应用会实时更新显示区域的内容。


### 使用 dcc.Graph 绘制图表

dcc.Graph 是 dash.dcc 中最常用的组件之一，用于绘制各种图表。

以下是一个使用 dcc.Graph 绘制折线图的示例：


## 实例

以上实例中，我们使用 plotly.express 创建了一个简单的折线图，并通过 dcc.Graph 组件将其显示在应用中。


### 使用 dcc.Dropdown 创建下拉菜单

dcc.Dropdown 组件允许用户从多个选项中选择一个。

以下是一个使用 dcc.Dropdown 的示例：


## 实例

以上实例中，我们创建了一个下拉菜单，当用户选择一个选项时，应用会显示用户选择的内容。


## dash.dcc 组件的常见属性和回调

dash.dcc 组件的属性非常丰富，每个组件都有其特定的属性。

以下是一些常见组件的属性：

- dcc.Input： id：组件的唯一标识符。 type：输入类型，如 text、number 等。 value：输入框的当前值。
- dcc.Dropdown： id：组件的唯一标识符。 options：下拉菜单的选项列表，每个选项是一个字典，包含 label 和 value。 value：当前选中的值。
- dcc.Graph： id：组件的唯一标识符。 figure：要显示的图表对象，通常由 plotly.express 或 plotly.graph_objects 创建。
- dcc.Slider： id：组件的唯一标识符。 min：滑块的最小值。 max：滑块的最大值。 value：滑块的当前值。


### 回调函数

在 Dash 中，回调函数用于处理用户交互。回调函数通过 @app.callback 装饰器定义，并指定输入和输出组件。

以下是一个简单的回调函数示例：


## 实例

以上实例中，回调函数 update_output 会在 input-component 的值发生变化时被调用，并将新的值传递给 output-component。


## 实际应用案例

dash.dcc 组件在实际项目中有广泛的应用。以下是一个实际应用案例，展示了如何使用 dash.dcc 组件构建一个交互式数据可视化应用。


### 交互式数据可视化应用

假设我们有一个数据集，包含不同城市的温度和湿度数据。我们可以使用 dash.dcc 组件构建一个交互式应用，允许用户选择城市并查看相应的温度和湿度图表。


## 实例

以上实例中，用户可以通过下拉菜单选择城市，应用会根据用户的选择更新温度和湿度的柱状图。


## 复习重点

- 能说明 `Dash 常用交互组件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
