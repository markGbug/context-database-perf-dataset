# Dash：Dash 样式设计

- 来源：[Dash 样式设计](https://www.runoob.com/dash/dash-css.html)
- 分类：Python / 数据科学
- 技术：Dash
- 笔记类型：学习笔记
- 章节序号：3804

## 本章内容

在开发交互式 Web 应用程序时，Dash 不仅允许你使用 Python 来构建复杂的应用程序，还提供了丰富的样式设计选项，使你的应用程序看起来更加专业和美观。

在 Dash 中，样式设计是通过 CSS 实现的。Dash 提供了多种方式来设置组件的样式，包括：

- 内联样式：通过 style 属性直接设置组件的样式。
- 外部 CSS 文件：通过加载外部 CSS 文件设置全局样式。
- Dash Bootstrap Components：使用 Bootstrap 风格的组件和样式。
- Dash DAQ：用于创建数据采集和控制应用的样式组件。


## 1. 内联样式

通过 style 属性可以直接为组件设置 CSS 样式。style 是一个字典，键是 CSS 属性，值是 CSS 值。


## 实例

运行效果：

- 背景颜色为浅蓝色，内边距为 20px，圆角为 10px，文字居中。
- 标题文字颜色为深蓝色。


## 2. 外部 CSS 文件

通过加载外部 CSS 文件，可以为整个应用设置全局样式。

- 创建一个 CSS 文件（如 assets/styles.css）。
- 在 Dash 应用中加载 CSS 文件。

CSS 文件示例 (assets/styles.css)：


## 实例：assets/styles.css 文件

Dash 使用 css 文件：


## 实例

运行效果：

- 应用加载 assets/styles.css 文件中的样式。
- h1 标题颜色为深蓝色，居中显示。
- Div 背景颜色为浅蓝色，带内边距和圆角。


## 3. Dash Bootstrap Components

Dash Bootstrap Components（dash-bootstrap-components）是一个第三方库，提供了 Bootstrap 风格的组件和样式。它可以帮助快速构建美观的 Dash 应用。

```text
pip install dash-bootstrap-components
```


## 实例

运行效果：

- 使用 Bootstrap 主题样式。
- 标题居中显示，颜色为主题蓝色。
- 卡片组件带有标题和内容，样式美观。


## 4. Dash DAQ

Dash DAQ 是一个用于创建数据采集和控制应用的组件库，提供了丰富的样式组件。

```text
pip install dash-daq
```


## 实例

运行效果：

- 显示一个温度计和一个压力表，样式美观。
- 组件居中显示，带外边距。


## 复习重点

- 能说明 `Dash 样式设计` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
