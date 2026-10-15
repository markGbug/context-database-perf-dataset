# Dash：Dash 常用 HTML 组件

- 来源：[Dash 常用 HTML 组件](https://www.runoob.com/dash/dash-html-component.html)
- 分类：Python / 数据科学
- 技术：Dash
- 笔记类型：练习笔记
- 章节序号：3798

## 本章内容

Dash 的核心组件之一是 HTML 组件，这些组件允许你在应用中嵌入标准的 HTML 元素。

本文将详细介绍 Dash 中常用的 HTML 组件。


## 1. 引入 HTML 组件

在 Dash 的最新版本中，HTML 组件的引入方式有所变化，我们可以直接从 dash 模块中导入 html 组件，而不需要像以前那样从 dash_html_components 中导入。

```text
from dash import html
```


### 常用 HTML 组件


## 2. 常用的 HTML 组件


### 2.1 html.Div

html.Div 是 Dash 中最常用的 HTML 组件之一，它用于创建一个 div 元素。div 元素通常用于将内容分组，并且可以通过 CSS 进行样式设置。


## 实例

在这个例子中，html.Div 包含了一个标题 (html.H1) 和一个段落 (html.P)。


### 2.2 html.H1 到 html.H6

html.H1 到 html.H6 用于创建不同级别的标题。H1 是最高级别的标题，H6 是最低级别的标题。


## 实例


### 2.3 html.P

html.P 用于创建一个段落 (<p> 元素)。


## 实例


### 2.4 html.A

html.A 用于创建一个超链接 (<a> 元素)。你可以通过 href 属性指定链接的目标 URL。


## 实例


### 2.5 html.Img

html.Img 用于在页面中插入图片 (<img> 元素)。你需要通过 src 属性指定图片的 URL。


## 实例


### 2.6 html.Ul 和 html.Li

html.Ul 用于创建一个无序列表 (<ul> 元素)，而 html.Li 用于创建列表项 (<li> 元素)。


## 实例


### 2.7 html.Ol

html.Ol 用于创建一个有序列表 (<ol> 元素)。


## 实例


### 2.8 html.Br

html.Br 用于在页面中插入一个换行符 (<br> 元素)。


## 实例


### 2.9 html.Hr

html.Hr 用于在页面中插入一条水平线 (<hr> 元素)。


## 实例


### 2.10 html.Span

html.Span 用于创建一个内联容器 (<span> 元素)，通常用于对文本的一部分进行样式设置。


## 实例


## 3. 使用样式

Dash 的 HTML 组件支持通过 style 属性来设置 CSS 样式。style 属性接受一个字典，其中键是 CSS 属性，值是相应的 CSS 值。


## 后续章节

- 实例
- 实例
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Dash 常用 HTML 组件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
