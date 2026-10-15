# Next.js：Next.js 组件与布局

- 来源：[Next.js 组件与布局](https://www.runoob.com/nextjs/nextjs-components-layout.html)
- 分类：前端开发
- 技术：Next.js
- 笔记类型：学习笔记
- 章节序号：3031

## 本章内容

Next.js 的组件与布局功能为开发者提供了强大的工具，帮助构建模块化、可维护的 Web 应用。

在 Next.js 13 中，app 目录替代了传统的 pages 目录，用于管理路由和页面结构。app 目录引入了更灵活的布局、路由、数据获取机制，以及增强的并行渲染能力。

app 目录结构示例:

```text
├── app/
│   ├── page.js           # 默认首页
│   ├── about/
│   │   ├── page.js       # About 页
│   └── layout.js         # 根布局
└── public/                # 静态文件目录
```


## 组件

组件是构建 Next.js 应用的基本单元。它们可以是页面组件、UI 组件或功能组件。

在 Next.js 中，所有页面和布局基本上都是 React 组件。你可以像在任何 React 应用中一样创建和使用组件。


### 页面组件

页面组件是 Next.js 中路由的基础，每个页面组件对应一个路由。

页面组件通常存放在 app 或 pages 目录下。


## 实例


### UI 组件

UI 组件是可复用的界面元素，例如按钮、卡片、导航栏等。

UI 组件通常存放在 components 目录下。


## 实例


### 功能组件

功能组件是实现特定功能的组件，例如数据获取、状态管理等。

功能组件通常存放在 hooks 或 utils 目录下。


## 实例


### 实例

创建组件：在 app/components/ 目录下创建 Hello.js，代码如下：


## 实例

使用组件：在 app 目录下，页面组件会从 page.js 中导出，你可以在其中使用组件：


## 实例


## 布局

布局是用于定义页面结构的组件，通常包含页眉、页脚、导航栏等公共元素。


### 全局布局

全局布局适用于整个应用程序，通常定义在 app/layout.js或 _app.js 中。


## 实例


### 嵌套布局

嵌套布局允许为不同的路由段定义不同的布局。

在 app 目录中，每个路由段可以包含一个 layout.js 文件。

```text
app/
├── layout.js        // 根布局
├── about/
│   ├── layout.js    // /about 的布局
│   └── page.js      // /about 页面
└── dashboard/
    ├── layout.js    // /dashboard 的布局
    └── page.js      // /dashboard 页面
```


## 实例


### 动态布局

动态布局允许根据条件动态选择布局。


## 实例


## 特殊文件（旧版本）

Next.js 提供了一些特殊文件，用于定义全局布局、文档结构和错误页面。


### _app.js

_app.js 是 Next.js 的全局组件，用于包装所有页面组件。


## 实例


### _document.js

_document.js 用于自定义 HTML 文档结构。


## 实例


### _error.js

_error.js 用于自定义错误页面。


## 实例


## 复习重点

- 能说明 `Next.js 组件与布局` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
