# Tailwind CSS：Tailwind CSS 深色模式

- 来源：[Tailwind CSS 深色模式](https://www.runoob.com/tailwindcss/tailwindcss-darkmode.html)
- 分类：前端开发
- 技术：Tailwind CSS
- 笔记类型：学习笔记
- 章节序号：3104

## 本章内容

深色模式（Dark Mode）是一种常见的用户界面设计趋势，提供暗色调的界面以减少眼睛疲劳，同时节省设备电量。

Tailwind CSS 支持深色模式（Dark Mode）的功能，使得开发者可以轻松地为网站创建深色版本，以适应用户的系统偏好。

Tailwind CSS 提供了一个名为 dark 的修饰符，允许你针对深色模式定义样式。

当用户设备或操作系统设置为深色模式时，带有 dark: 修饰符的样式将自动生效。

以下实例基于系统首选项的媒体查询设置样式：


## 实例

在浅色模式下：背景色为白色（bg-white），文本颜色为黑色（text-black）。

在深色模式下：背景色为黑色（dark:bg-black），文本颜色为白色（dark:text-white）。


## 启用深色模式

默认情况下，Tailwind 使用 media 策略来检测深色模式，即基于用户的系统首选项。

如果需要更细粒度的控制，也可以使用 class 策略。


### 1、在 tailwind.config.js 中启用深色模式


## 实例

- media 模式：根据用户操作系统的设置（通过媒体查询 prefers-color-scheme: dark）自动切换。
- class 模式：允许开发者通过在 html 或 body 标签上添加 dark 类手动切换深色模式。

两种模式的差异:


### 切换逻辑示例（class 模式）

如果要支持手动切换深色模式而不是依赖于操作系统首选项，请使用 class 策略代替 media 策略。

现在，dark:{class} 类将不再根据 prefers-color-scheme 起作用，而是当在 HTML 树中出现 dark 类时起作用：

```html
<!-- 不允许深色模式 -->
<html>
<body>
  <div class="bg-white dark:bg-black">...</div>
</body>
</html>

<!-- 允许深色模式 -->
<html class="dark">
<body>
  <div class="bg-white dark:bg-black">...</div>
</body>
</html>
```


## 实例


## 如何使用深色模式工具类


### 1、样式切换

使用 dark: 前缀指定深色模式下的样式。


## 实例


### 2、响应式与深色模式结合

响应式断点和深色模式可以同时使用：


## 实例

小屏幕下字体为 xl。

在深色模式中，小屏幕的字体颜色变为浅灰色。


### 3、交互状态与深色模式结合

你可以结合 hover, focus 等状态与深色模式应用样式：


## 实例


## 扩展深色模式

在某些情况下，你可能需要针对深色模式提供额外的颜色或样式，可以通过 theme.extend 自定义 Tailwind 配置。

```text
module.exports = {
  theme: {
    extend: {
      colors: {
        brand: {
          DEFAULT: '#1DA1F2',
          dark: '#0d74b8',
        },
      },
    },
  },
}
```

在 HTML 中使用扩展颜色：


## 实例


## 实例

以下是一个实现深色模式切换的完整示例：


## 实例


## 复习重点

- 能说明 `Tailwind CSS 深色模式` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
