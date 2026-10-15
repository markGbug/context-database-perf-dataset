# Tailwind CSS：Tailwind CSS 指令与函数

- 来源：[Tailwind CSS 指令与函数](https://www.runoob.com/tailwindcss/tailwindcss-functions-and-directives.html)
- 分类：前端开发
- 技术：Tailwind CSS
- 笔记类型：练习笔记
- 章节序号：3107

## 本章内容

Tailwind CSS 提供了一些非常有用的函数和指令，它们帮助开发者更好地管理样式和优化代码。

通过函数与指令，Tailwind 可以为你提供更多的控制权和灵活性，尤其是在定制样式、处理响应式设计、扩展功能等方面。

Tailwind CSS 提供了多种指令和函数来帮助开发者管理和定制样式：

- 使用 @tailwind 引入 Tailwind 的基础样式、组件样式和工具类。
- @apply 可以将多个工具类组合成自定义的类，避免样式重复。
- @layer 允许你在自定义 CSS 中组织和定义不同的层次样式。
- 使用内建的颜色、间距、透明度、边框圆角等函数，可以动态计算和生成样式。


## @tailwind 指令

@tailwind 指令用于在 CSS 文件中引入 Tailwind 的三大核心层：base, components 和 utilities。

- @tailwind base：引入 Tailwind 的基础样式（如浏览器的重置样式）。
- @tailwind components：引入组件样式，用于定义如按钮、卡片、表单等的基础样式。
- @tailwind utilities：引入工具类，Tailwind 样式库的核心部分，提供了用于布局、颜色、间距、边框等的低级实用类。

这些层定义了你在使用 Tailwind 时所需的所有基本样式、组件样式和工具类。

```text
/* 自定义样式中引入 Tailwind 样式 */
@tailwind base;          /* 引入基础样式 */
@tailwind components;    /* 引入组件样式 */
@tailwind utilities;     /* 引入工具类 */
```


### @apply 指令

@apply 指令用于在自定义 CSS 类中应用 Tailwind 的工具类。这允许你在保持 Tailwind 的可维护性和灵活性的同时，也可以将常用的样式组合在一起。

```html
.my-class {
  @apply <utility-class1> <utility-class2> ... ;
}
```


## 实例

通过使用 @apply，你可以将常用的类组合成一个自定义的 CSS 类，这样就能重复使用。


### @layer 指令

@layer 指令用于在 Tailwind 中定义层（layer），主要用于自定义扩展样式的组织。它通常用于创建自定义的组件、实用程序类等，以保持 CSS 文件的结构清晰。

- @layer components：定义自定义组件。
- @layer utilities：定义自定义工具类。
- @layer base：定义基础样式。

语法格式：

```text
@layer components {
  /* 在这里定义自定义的组件类 */
}

@layer utilities {
  /* 在这里定义自定义的工具类 */
}
```


## 实例


### @import 指令

在 Tailwind CSS 中，你还可以使用 @import 指令来引入其他 CSS 文件。虽然 Tailwind 本身不推荐你频繁使用 @import，但是它仍然支持这一功能。

语法格式：

```html
@import '<path-to-file>';
```


## Tailwind CSS 的函数

Tailwind CSS 中的函数主要用于动态生成样式，比如颜色、透明度、尺寸等的计算。它们让你能够在配置文件或自定义样式中做更多的计算和控制。


### 颜色函数 (Color Functions)

Tailwind 提供了一些内建的颜色函数，它们可以用来生成颜色的不同变体（如调暗、调亮等）。

- darken()：调暗颜色。
- lighten()：调亮颜色。
- opacity()：设置颜色的透明度。


## 实例


### 间距函数 (Spacing Functions)

Tailwind 提供了 rem, px, em 等单位的函数。你可以通过它们来计算动态的尺寸和间距值。


## 实例


### 边框圆角函数 (Border Radius Functions)

Tailwind CSS 中也可以使用函数来设置边框圆角。例如，使用 radius() 来计算不同的圆角。


## 实例


### 自定义函数 (Custom Functions)

Tailwind CSS 允许你定义和使用自定义的函数。你可以在 tailwind.config.js 中使用 theme 函数来访问并操作 Tailwind 的设计系统。例如，你可以动态地生成颜色、间距、字体等。


## 实例


### Tailwind CSS 的常用内建函数

Tailwind CSS 内建了很多函数来帮助你在构建自定义样式时做计算。

以下是一些常见的内建函数：

rem() 示例:

```text
/* 将数字 16 转换为 rem 单位 */
.my-class {
  font-size: rem(16);  /* 结果为 1rem */
}
```

em() 示例:

```text
/* 将数字 16 转换为 em 单位 */
.my-class {
  padding: em(16);  /* 结果为 1em */
}
```

px() 示例:

```text
/* 使用 px() 函数生成固定像素 */
.my-class {
  margin: px(16);  /* 结果为 16px */
}
```

calc() 示例:

```text
/* 使用 calc() 函数动态计算 */
.my-class {
  width: calc(100% - px(20));  /* 结果为 100% - 20px */
}
```

theme() 示例:

```text
/* 使用 theme() 函数访问 Tailwind 主题配置 */
.my-class {
  background-color: theme('colors.green.500');  /* 结果为 #10b981 */
}
```

clamp() 示例:

```text
/* 使用 clamp() 设置字体大小，基于视口宽度变化 */
.my-class {
  font-size: clamp(1rem, 5vw, 3rem);  /* 最小 1rem，最大 3rem，视口宽度介于其间时动态变化 */
}
```


### 使用条件运算符和函数组合

在 Tailwind 中，许多功能可以与条件运算符一起使用。结合响应式设计和状态类（如 hover:, focus:）时，你可以动态地应用这些样式。

例如，你可以结合 @apply 和响应式设计来实现某些功能：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Tailwind CSS 指令与函数` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
