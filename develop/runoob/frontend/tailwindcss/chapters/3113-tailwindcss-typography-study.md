# Tailwind CSS：Tailwind CSS 排版

- 来源：[Tailwind CSS 排版](https://www.runoob.com/tailwindcss/tailwindcss-typography.html)
- 分类：前端开发
- 技术：Tailwind CSS
- 笔记类型：学习笔记
- 章节序号：3113

## 本章内容

Tailwind CSS 的 Typography（排版）功能是一组实用工具，帮助开发者高效地设计文本样式。它包括设置字体、字重、行高、字距、文本对齐等基本排版属性，同时还支持复杂的排版需求，如响应式字体大小、文本阴影、文本装饰等。


### 1. 字体（Font Family）

Tailwind 提供了一些工具类来设置字体系列（font-family），可以通过类名轻松应用。

- font-sans: 设置无衬线字体。
- font-serif: 设置衬线字体。
- font-mono: 设置等宽字体。


## 实例


### 2. 字体大小（Font Size）

字体大小可以通过 Tailwind 的 text-* 工具类进行控制，支持从 text-xs 到 text-9xl 的多种大小，甚至可以自定义字体大小。

- text-xs, text-sm, text-base, text-lg, text-xl, text-2xl, ..., text-9xl


## 实例


### 3. 字体粗细（Font Weight）

字体粗细可以通过 font-* 工具类来控制，Tailwind 提供了从 font-thin 到 font-black 的多种粗细选项。

- font-thin: 超细字体
- font-light: 轻字体
- font-normal: 普通字体
- font-medium: 中等粗细字体
- font-semibold: 半粗字体
- font-bold: 粗体
- font-extrabold: 更粗字体
- font-black: 极粗字体


## 实例


### 4. 行高（Line Height）

行高（即行间距）可以通过 leading-* 工具类来控制。Tailwind 提供了多种行高选项，从 leading-none 到 leading-loose，可以根据需要调整。

- leading-none: 行高为 1
- leading-tight: 紧凑行高
- leading-snug: 稍微紧凑行高
- leading-normal: 默认行高
- leading-relaxed: 放松行高
- leading-loose: 松散行高


## 实例


### 5. 字间距（Letter Spacing）

字间距可以通过 tracking-* 工具类来控制。常用的字间距选项包括 tracking-tight、tracking-normal 和 tracking-wide，用于调整字母之间的空隙。

- tracking-tight: 紧凑字间距
- tracking-normal: 默认字间距
- tracking-wide: 宽字间距
- tracking-wider: 更宽字间距
- tracking-wide: 极宽字间距


## 实例


### 6. 文本颜色（Text Color）

Tailwind 提供了多种文本颜色类，允许你为文本设置不同的颜色。你可以使用 text-* 工具类来设置颜色。

- text-gray-500: 中等灰色
- text-red-500: 红色
- text-blue-500: 蓝色
- text-green-500: 绿色


## 实例


### 7. 文本对齐（Text Alignment）

Tailwind 提供了简单的工具类来控制文本对齐方式。你可以使用 text-left、text-center 或 text-right 来设置文本的对齐方式。

- text-left: 左对齐
- text-center: 居中对齐
- text-right: 右对齐


## 实例


### 8. 文本修饰（Text Decoration）

你可以使用 underline, line-through 和 no-underline 来控制文本的下划线和删除线。

- underline: 添加下划线
- line-through: 添加删除线
- no-underline: 去除下划线


## 实例


### 9. 文本装饰（Text Transform）

Tailwind 提供了 uppercase、lowercase 和 capitalize 类来控制文本的大小写转换。

- uppercase: 全部大写
- lowercase: 全部小写
- capitalize: 每个单词首字母大写


## 实例


### 10. 文本阴影（Text Shadow）

Tailwind 允许你为文本添加阴影效果，使用 text-shadow 工具类。

- text-shadow: 设置简单的文本阴影（此功能需要自定义插件或扩展）。


## 实例


### 11. 响应式字体（Responsive Font Size）

Tailwind 支持响应式设计，你可以在不同屏幕大小下设置不同的字体大小。通过为不同的屏幕尺寸添加前缀如 sm:, md:, lg:, xl: 等来控制字体大小。


## 实例


## 复习重点

- 能说明 `Tailwind CSS 排版` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
