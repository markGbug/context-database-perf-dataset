# Next.js：Next.js 图片和字体

- 来源：[Next.js 图片和字体](https://www.runoob.com/nextjs/nextjs-images-and-fonts.html)
- 分类：前端开发
- 技术：Next.js
- 笔记类型：练习笔记
- 章节序号：3030

## 本章内容

Next.js 提供了内置的图片和字体优化功能，旨在提升应用性能和用户体验。

Next.js 的图片和字体优化功能为开发者提供了强大的工具，帮助构建高性能、用户体验优秀的 Web 应用。


## 静态资源管理

Next.js 允许将静态资源（如图片、字体等）存放在 public 目录下。

这些资源可以通过 /filename 直接访问。

目录结构示例：

```text
my-next-app/
├── app/
├── public/
│   ├── images/
│   │   └── logo.png
│   └── fonts/
│       └── my-font.woff2
├── package.json
└── next.config.js
```

public/images/logo.png 可以通过 /images/logo.png 访问。


## 图片优化

Next.js 提供了 <Image> 组件，用于优化图片加载。它扩展了 HTML 的 <img> 元素，提供了以下功能：

- 尺寸优化：自动为不同设备提供正确尺寸的图片，支持现代图片格式（如 WebP）。
- 视觉稳定性：防止图片加载时的布局偏移（Layout Shift）。
- 更快加载：使用原生浏览器懒加载，仅在图片进入视口时加载。
- 资源灵活性：支持按需调整图片尺寸，即使是远程图片。


### 使用 <Image> 组件

从 next/image 导入 <Image> 组件，并在组件中使用。


## 实例


### 本地图片

本地图片可以直接从 public 目录引用。


## 实例


### 远程图片

远程图片需要手动指定 width 和 height，以避免布局偏移。


## 实例


### 配置远程图片

在 next.config.js 中配置允许的远程图片域名。


## 实例


## 字体优化

Next.js 提供了 next/font 模块，用于优化字体加载。它支持自动托管字体文件，提升隐私和性能。


### 使用 Google 字体

从 next/font/google 导入字体，并应用到 HTML 元素。


## 实例

如果使用非可变字体，需要指定 weight：


## 实例


### 使用本地字体

从 next/font/local 导入本地字体文件。


## 实例

如果使用多个字体文件：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Next.js 图片和字体` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
