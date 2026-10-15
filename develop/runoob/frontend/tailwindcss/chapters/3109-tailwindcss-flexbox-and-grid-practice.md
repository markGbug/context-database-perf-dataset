# Tailwind CSS：Tailwind CSS 与 Flexbox 和 Grid 布局

- 来源：[Tailwind CSS Flexbox & Grid](https://www.runoob.com/tailwindcss/tailwindcss-flexbox-and-grid.html)
- 分类：前端开发
- 技术：Tailwind CSS
- 笔记类型：练习笔记
- 章节序号：3109

## 本章内容

Tailwind CSS 提供了强大的工具类来管理布局，特别是 Flexbox 和 Grid。

Flexbox 和 Grid 这些工具类使得你可以非常高效地创建响应式、灵活的布局，而无需编写自定义的 CSS。

Tailwind CSS 的理念是通过低层级的实用类（utility-first）来控制布局，灵活组合类以满足不同的设计需求。


## 1、Flexbox 布局

Flexbox 是一种布局模式，可以帮助开发者创建一维的（水平或垂直）布局。

Tailwind CSS 提供了多个简洁的工具类来控制 Flexbox 布局的各个方面，包括方向、对齐、伸缩等。


### 设置 Flex 容器

要创建一个 Flexbox 布局，首先需要将元素设为 flex 容器。


## 实例

flex 将元素的 display 设置为 flex，即启用 Flexbox 布局。

flex 项初始大小的工具类及其对应的 CSS 属性：


## 实例


### Flex 方向

flex-direction 控制主轴的方向（即 Flex 容器内项目排列的方向）。

Tailwind 提供了以下工具类来设置方向：

- flex-row: 默认值，子项按水平方向从左到右排列。
- flex-row-reverse: 子项按水平方向从右到左排列。
- flex-col: 子项按垂直方向从上到下排列。
- flex-col-reverse: 子项按垂直方向从下到上排列。


## 实例


### Flex 包裹（Flex Wrap）

默认情况下，Flexbox 容器中的项目会在单行内排列。

如果你希望它们换行，可以使用 flex-wrap 工具类。

- flex-wrap: 允许项目换行。
- flex-nowrap: 禁止项目换行。
- flex-wrap-reverse: 反向换行。


## 实例


### Flex 项目的伸缩性

Flexbox 允许元素的大小根据可用空间进行伸缩。

Tailwind CSS 提供了以下工具类来控制伸缩：


## 实例


### flex-grow 属性

以下是控制 flex 项的 flex-grow 属性的工具类及其对应的 CSS 属性：


## 实例


### flex-shrink 属性

以下是控制 flex 项的 flex-shrink 属性的工具类及其对应的 CSS 属性：


## 实例


## 排序

以下是用于控制 flex 项或 grid 项排列顺序的工具类及其对应的 CSS 属性：


## 实例


## Grid (网格) 布局

Grid 是另一种布局模型，允许你在行和列中精确地定位元素，并且能够轻松创建复杂的布局。

Tailwind CSS 提供了强大的工具类来操作网格布局。

以下是 Tailwind CSS 中用于指定网格布局中列数的工具类及其对应的 CSS 属性：


## 实例

- grid: 启用 Grid 布局。
- grid-cols-{n}: 设置网格的列数。
- gap-{size}: 设置列和行之间的间距。


### Grid 行与列

通过 grid-template-columns 和 grid-template-rows 控制列和行的宽度和高度。Tailwind 提供了如下的工具类来控制：

- grid-cols-{n}: 设置网格的列数（例如 grid-cols-3 表示三列）。
- grid-rows-{n}: 设置网格的行数（例如 grid-rows-2 表示两行）。
- col-span-{n}: 设置一个项目占用多少列。
- row-span-{n}: 设置一个项目占用多少行。


## 实例


## 实例


## 实例


### Grid 项目的定位

grid-column 和 grid-row 控制每个项目在网格中的位置。

你可以通过以下工具类来指定：

- col-start-{n}: 设置项目从第 n 列开始。
- col-end-{n}: 设置项目到第 n 列结束。
- row-start-{n}: 设置项目从第 n 行开始。
- row-end-{n}: 设置项目到第 n 行结束。


## 实例


## 后续章节

- 实例
- 对齐和分布
- 实例
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Tailwind CSS Flexbox & Grid` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
