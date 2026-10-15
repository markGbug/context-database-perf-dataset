# Tailwind CSS：Tailwind CSS 表格

- 来源：[Tailwind CSS 表格](https://www.runoob.com/tailwindcss/tailwindcss-table.html)
- 分类：前端开发
- 技术：Tailwind CSS
- 笔记类型：练习笔记
- 章节序号：3112

## 本章内容

Tailwind CSS 提供了一套方便的工具类，用于创建和自定义表格。

通过这些工具类，你可以轻松地对表格进行样式控制，包括边框、间距、对齐方式、字体样式等。

接下来，我们将详细介绍如何使用 Tailwind CSS 来创建和自定义表格。


## 基础表格样式

Tailwind CSS 提供了一些基础类，用于控制表格的外观和布局。常用的工具类包括 table-auto 和 table-fixed，这两个类用来设置表格的布局。

- table-auto：默认布局，表格的列宽由内容自动决定。
- table-fixed：表格列宽固定。所有列的宽度都会根据表格的总宽度平分，适用于具有统一列宽的表格。

使用 table-auto 允许表格自动调整列宽以适应单元格内容。


## 实例

使用 table-fixed 允许表格忽略内容，对列使用固定宽度。第一行的宽度将为整个表格设置列宽。


## 实例


## 边框和间距

Tailwind 提供了许多工具类来控制表格的边框、内外边距以及其他布局细节。

你可以使用 border, border-collapse, border-spacing 等类来控制表格的边框样式。

- border：为表格添加边框。
- border-collapse：控制表格单元格的边框是否合并。
- border-spacing：设置单元格之间的间距。


## 实例


### 内外边距

你可以使用 px-*, py-* 类来设置表格单元格的 内边距，以及 m-* 和 p-* 类来设置表格的外边距。


## 实例


## 对齐和文字样式

Tailwind 提供了一些类来控制表格单元格内容的对齐和字体样式，如：

- text-left, text-center, text-right：控制文本对齐。
- font-semibold, font-bold：控制字体粗细。
- uppercase, lowercase, capitalize：控制文本的大小写。


## 实例


## 合并单元格

Tailwind CSS 支持通过 HTML 属性来设置 合并单元格，如 colspan 和 rowspan。


## 实例


## 响应式表格

你还可以使用 Tailwind CSS 的响应式设计类，来在不同屏幕尺寸下控制表格的布局。

例如，使用 sm:, md:, lg: 前缀来设置不同屏幕下的显示方式。


## 实例


## 表格标题

使用 caption-top 将标题元素定位在表格的顶部。


## 实例

使用 caption-bottom 将标题元素定位在表格的底部。


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Tailwind CSS 表格` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
