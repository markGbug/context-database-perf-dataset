# Next.js：Next.js 项目说明

- 来源：[Next.js 项目说明](https://www.runoob.com/nextjs/nextjs-project-intro.html)
- 分类：前端开发
- 技术：Next.js
- 笔记类型：练习笔记
- 章节序号：3025

## 本章内容

Next.js 项目由多个文件和文件夹组成，每个部分都有其特定的作用。

以下是对 Next.js 项目代码的基本解析，帮助你理解项目的结构和各个部分的功能。

从 Next.js 13 开始，Next.js 引入了基于文件系统的 App Router（app 目录），取代了传统的 pages 目录。新的 app 目录提供了更强大的功能，如嵌套路由、布局、服务器组件等。


## 项目结构

一个使用 app 目录的 Next.js 项目通常包含以下文件和文件夹：

```text
my-next-app/
├── node_modules/       # 项目依赖的第三方库
├── public/             # 静态资源文件夹
│   ├── favicon.ico     # 网站图标
│   └── ...             # 其他静态资源（如图片、字体等）
├── app/                # 应用路由目录（核心）
│   ├── layout.js       # 根布局组件
│   ├── page.js         # 首页组件
│   ├── about/          # 关于页面
│   │   └── page.js     # 关于页面组件
│   ├── blog/           # 博客页面
│   │   ├── page.js     # 博客列表页
│   │   └── [slug]/     # 动态路由
│   │       └── page.js # 博客详情页
│   └── ...             # 其他页面和路由
├── components/         # 可复用的 React 组件
├── styles/             # 样式文件
├── utils/              # 工具函数
├── package.json        # 项目配置和依赖管理
├── package-lock.json   # 依赖的精确版本锁定文件
├── next.config.js      # Next.js 配置文件
└── README.md           # 项目说明文档
```


## 核心文件解析


### app/layout.js

app/layout.js 是根布局文件，用于定义整个应用的布局结构。

app/layout.js 包裹所有页面，可以包含全局样式、元数据等。


## 实例


### app/page.js

app/page.js 是首页文件，对应路由 /。


## 实例


### app/about/page.js

app/about/page.js 是关于页面文件，对应路由 /about。


## 实例


### app/blog/[slug]/page.js

app/blog/[slug]/page.js 是动态路由文件，用于处理类似 /blog/:slug 的路由。


## 实例


### app/loading.js

app/loading.js 加载状态文件，用于在页面加载时显示加载状态。


## 实例


### app/error.js

app/error.js 是错误页面文件，用于捕获并显示错误。


## 实例


### app/not-found.js

app/not-found.js 是 404 页面文件，用于显示未找到的页面。


## 实例


## 新特性解析


### 1、服务器组件（Server Components）

Next.js 13 默认使用服务器组件，减少了客户端 JavaScript 的加载量。

服务器组件可以直接访问后端数据，无需额外的 API 调用。


## 实例


### 2、客户端组件（Client Components）

如果需要使用 React 状态或浏览器 API，可以将组件标记为客户端组件。

使用 'use client' 指令。


## 实例


### 3、嵌套布局（Nested Layouts）

可以在 app 目录中创建嵌套布局，每个子目录可以有自己的布局文件。

例如：

app/dashboard/layout.js：仪表盘页面的布局。

app/dashboard/page.js：仪表盘页面的内容。


### 4、流式渲染（Streaming）

Next.js 13 支持流式渲染，可以在页面加载时逐步渲染内容。


## 实例


## 后续章节

- 运行项目

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Next.js 项目说明` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
