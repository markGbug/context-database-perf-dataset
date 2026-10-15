# Tailwind CSS：Tailwind CSS 配置

- 来源：[Tailwind CSS 配置](https://www.runoob.com/tailwindcss/tailwindcss-config.html)
- 分类：前端开发
- 技术：Tailwind CSS
- 笔记类型：学习笔记
- 章节序号：3100

## 本章内容

Tailwind CSS 的核心配置文件为 tailwind.config.js。

tailwind.config.js 是 Tailwind CSS 的配置文件，用于定制化 Tailwind 的默认配置。

通过修改 tailwind.config.js 文件，开发者可以自定义颜色、间距、字体、断点等设计系统，满足特定项目需求。


### 创建配置文件

使用 Tailwind CSS 的 CLI 工具可以快速生成一个基础的 tailwind.config.js 文件。

在项目根目录下运行以下命令：

```text
npx tailwindcss init
```

这将创建一个包含基本配置的 tailwind.config.js 文件。


### 基本结构

以下是一个典型的 tailwind.config.js 文件的结构：


## 实例

以上代码告诉 Tailwind CSS 扫描 src 目录下的所有 .html, .js, 和 .vue 文件。


## 主要配置项


### 1、配置模板路径：content

```text
content: [
  "./index.html", // 单文件路径
  "./src/**/*.{html,js,ts,jsx,tsx}", // 包含多个文件类型的路径
],
```

这将告诉 Tailwind CSS 扫描 src 目录下的所有 .html、.js、.ts\.jsx 和 .tsx 文件。

content 字段用于指定 Tailwind 的模板文件路径，Tailwind 会扫描这些文件以生成必要的样式，减少生成的 CSS 文件体积，只生成模板文件中使用的样式，防止未使用的样式被编译到最终输出中。


### 2、自定义主题：theme

在 theme 部分，你可以定义颜色、字体、间距、边框大小等。

例如，扩展默认的颜色或添加新的颜色：

```text
theme: {
  extend: {
    colors: {
      cyan: '#9cdbff',
    }
  }
}
```

这将添加一个名为 cyan 的新颜色，你可以在项目中使用 bg-cyan 这样的类名。


## 实例

通过 theme.colors 定义颜色，并在样式中引用。

```text
theme: {
  extend: {
    colors: {
      brand: {
        light: '#93C5FD',
        DEFAULT: '#3B82F6',
        dark: '#1E40AF',
      },
    },
  },
}
```


## 实例

通过 darkMode 开启 Tailwind 的暗色模式支持。

```text
module.exports = {
  darkMode: 'class', // 或 'media'
  theme: {
    extend: {
      colors: {
        background: {
          light: '#FFFFFF',
          dark: '#000000',
        },
      },
    },
  },
}
```


## 实例


### 3、配置变体：variants

variants 选项允许你定义哪些状态（如 hover、focus 等）应该被包含在最终的 CSS 中。

你可以扩展或覆盖默认的变体：

```text
variants: {
  extend: {
    borderColor: ['focus-visible'],
    opacity: ['disabled'],
  }
}
```


### 4、使用插件：plugins

plugins 选项允许你添加自定义的工具类。

这些插件可以是 Tailwind CSS 官方提供的，也可以是社区创建的，格式如下：

```text
plugins: [
  require('some-tailwindcss-plugin')
]
```

使用插件实例：


## 实例

引入社区插件：


## 实例


## Tailwind CSS 配置

默认情况下，Tailwind 会在项目根目录中查找 tailwind.config.js 文件，您可以在其中设置自己需要的配置信息：


## 实例

下表列出了 tailwind.config.js 文件的配置选项及使用说明：

通过 tailwind.config.js，可以轻松自定义 Tailwind CSS 的功能与样式，适配各种设计需求。合理利用扩展（extend）、插件（plugins）以及主题配置（theme）等特性，能够大幅提升项目的开发效率和样式灵活性。


## 复习重点

- 能说明 `Tailwind CSS 配置` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
