# Dash：Dash 安装指南

- 来源：[Dash 安装](https://www.runoob.com/dash/dash-install.html)
- 分类：Python / 数据科学
- 技术：Dash
- 笔记类型：学习笔记
- 章节序号：3795

## 本章内容

Dash 是一个基于 Python 的开源框架，用于构建交互式的 Web 应用程序，适合用于数据分析和可视化，因为它允许开发者通过简单的 Python 代码创建复杂的用户界面。

Dash 的核心组件包括 dash、dash-core-components、dash-html-components 和 dash-bootstrap-components，这些组件共同构成了一个强大的工具集，帮助开发者快速构建数据驱动的 Web 应用。

Dash 是一个基于 Python 的框架，因此安装过程非常简单，主要通过 pip 完成。


### 安装 Dash 的前提条件

在安装 Dash 之前，你需要确保你的系统已经安装了 Python，Dash 支持 Python 3.6 及以上版本。如果你还没有安装 Python，可以从 Python 官方网站 下载并安装适合你操作系统的版本。

页可以参阅我们的 Python 教程。


## 安装 Dash

安装 Dash 非常简单，可以通过 Python 的包管理工具 pip 来完成。

pip 是 Python 的包管理工具，用于安装 Dash 及其依赖库。

确保已安装 pip，可以通过以下命令检查：

```text
pip --version
```

注意：Python 2.7.9 + 或 Python 3.4+ 以上版本都自带 pip 工具。

如果没有安装可以参考：Python pip 安装与使用。

打开终端或命令行工具，运行以下命令：

```text
pip install dash
或
pip3 install dash
```

这条命令会安装 Dash 的核心库及其依赖项，包括：

- dash：Dash 的核心库。
- dash-core-components：Dash 的核心组件库（如输入框、下拉菜单、图表等）。
- dash-html-components：Dash 的 HTML 组件库（如 div、h1、p 等）。
- dash-table：用于显示和操作表格数据的组件。

除了核心库外，Dash 还支持一些可选依赖库，用于增强功能。

以下是常用的可选库及其安装方法：

1、Plotly

Plotly 是 Dash 默认的图表渲染库。如果你需要使用 Plotly 创建图表，可以单独安装：

```text
pip install plotly
```

2、Pandas

Pandas 是一个强大的数据处理库，常用于与 Dash 结合使用。安装命令：

```text
pip install pandas
```

3、JupyterDash

如果你希望在 Jupyter Notebook 中使用 Dash，可以安装 jupyter-dash：

```text
pip install jupyter-dash
```

4、Dash Bootstrap Components

Dash Bootstrap Components 提供了 Bootstrap 风格的组件，用于快速构建美观的布局。安装命令：

```text
pip install dash-bootstrap-components
```


### 验证安装

安装完成后，你可以通过以下命令来验证 Dash 是否安装成功：


## 实例

如果安装成功，你将看到 Dash 的版本号输出，例如：

```text
3.2.0
```

此外，还可以使用以下命令查看 Dash 的详细安装信息：

```text
python -m pip show dash
```

该命令会显示 Dash 的版本号、安装位置及依赖信息。

注意： Dash 3.0 及以上版本已将 app.run_server() 替换为 app.run()，使用新版 Dash 时应采用新的启动方式。


## 复习重点

- 能说明 `Dash 安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
