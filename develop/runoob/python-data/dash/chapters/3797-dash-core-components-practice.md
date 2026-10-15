# Dash：Dash 核心组件

- 来源：[Dash 核心组件](https://www.runoob.com/dash/dash-core-components.html)
- 分类：Python / 数据科学
- 技术：Dash
- 笔记类型：练习笔记
- 章节序号：3797

## 本章内容

Dash 的核心组件是构建应用程序的基础，它们允许你创建用户界面并与数据进行交互。

Dash 通过 dash.html 和 dash.dcc 模块，你可以轻松地创建用户界面并与数据进行交互。

从 Dash 2.0 版本开始，dash_html_components 和 dash_core_components 已经被整合到 dash 主包中。

现在推荐直接从 dash 中导入 html 和 dcc，而不是使用旧的 dash_html_components 和 dash_core_components。


## Dash 核心组件概述

Dash 的核心组件可以分为两大类：dash.html 和 dash.dcc。dash.html 提供了 HTML 标签的 Python 封装，而 dash.dcc 则提供了更高级的交互式组件，如滑块、下拉菜单、图形等。


### 1. dash.html 组件

dash.html 模块提供了与 HTML 标签对应的 Python 类。这些类允许你以 Python 的方式编写 HTML 代码。例如，dash.html.Div 对应 HTML 的 <div> 标签，dash.html.H1 对应 <h1> 标签。


## 实例

dash.html 组件使得编写 HTML 结构变得非常简单和直观。

以上代码中，我们创建了一个包含标题、段落和两个 Span 元素的 Div 容器。


### 2. dash.dcc 组件

dash.dcc 模块提供了更高级的交互式组件，这些组件通常用于数据可视化和用户输入。常见的 dash.dcc 组件包括 Graph、Dropdown、Slider 等。


## 实例

在这个示例中，我们创建了一个包含柱状图和下拉菜单的布局。dcc.Graph 组件用于显示数据可视化图表，而 dcc.Dropdown 组件则允许用户从下拉菜单中选择选项。


## 核心组件的属性

每个 Dash 组件都有一些属性，这些属性用于控制组件的外观和行为。例如，dash.html.Div 的 children 属性用于指定其子元素，dash.dcc.Graph 的 figure 属性用于指定图表的数据和布局。


### 常用属性

- children: 用于指定组件的子元素。大多数组件都有这个属性。
- id: 用于唯一标识组件，通常在回调函数中使用。
- style: 用于设置组件的 CSS 样式。
- className: 用于指定组件的 CSS 类名。


## 实例

以上代码中，我们使用 style 属性来设置标题的颜色和字体大小，并使用 className 属性为段落指定了一个 CSS 类名。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Dash 核心组件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
