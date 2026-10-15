# Tailwind CSS：Tailwind CSS 边框

- 来源：[Tailwind CSS 边框](https://www.runoob.com/tailwindcss/tailwindcss-borders.html)
- 分类：前端开发
- 技术：Tailwind CSS
- 笔记类型：练习笔记
- 章节序号：3115

## 本章内容

在 Tailwind CSS 中，边框（Borders）是布局和设计中常见的样式，用于为元素添加边界或分隔线。

Tailwind 提供了多种边框工具类，帮助你控制边框的宽度、颜色、样式、半径以及各个方向的边框。


### 边框宽度（Border Width）

边框宽度决定了元素的边框线条的粗细。Tailwind CSS 提供了不同的边框宽度值，允许你快速控制元素边框的样式。


### 边框颜色（Border Color）

通过使用 border-{color} 工具类，你可以设置元素边框的颜色。Tailwind CSS 提供了大量的预设颜色，可以直接使用，也支持自定义颜色。

```html
<div class="border-2 border-red-500 p-4">
  红色边框，宽度为 2px
</div>
```


### 边框样式（Border Style）

Tailwind CSS 也支持设置边框的样式，如实线、虚线、点线等。通过 border-{style} 工具类，你可以控制边框的显示样式。

```html
<div class="border-4 border-dashed border-blue-400 p-4">
  蓝色虚线边框，宽度为 4px
</div>
```


### 边框半径（Border Radius）

通过设置 border-radius，你可以控制元素的圆角效果。Tailwind CSS 提供了多种边框半径值，并允许你在不同方向上设置不同的圆角。

```html
<div class="border-4 border-gray-400 rounded-lg p-6">
  大圆角边框
</div>
```


### 四个方向的边框控制

你可以单独控制每个方向的边框（上、右、下、左），如：border-t-2 控制顶部边框的宽度，border-r-4 控制右侧边框的宽度，等等。

```html
<div class="border-t-4 border-r-2 border-b-1 border-l-3 border-blue-500 p-4">
  自定义各个方向的边框
</div>
```


### 统一的边框控制（Border）

如果你想要为所有边框设置相同的样式，使用 border 工具类即可。可以结合其他工具类控制颜色、样式和宽度。

```html
<div class="border-4 border-solid border-green-500 p-4">
  绿色实线边框，宽度为 4px
</div>
```


### 内边框和外边框（Box Model）

Tailwind CSS 还提供了控制 盒模型 的工具类，尤其是内外边框、外边距和内填充等。

```html
<div class="box-border border-4 border-red-500 p-4">
  边框包含在内的盒子模型
</div>
```


### 结合所有边框工具的综合实例


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Tailwind CSS 边框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
