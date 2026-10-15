# Vue3：路由跳转

- 来源：[路由跳转](https://www.runoob.com/vue3/vue3-blog-vue-router.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：学习笔记
- 章节序号：3241

## 本章内容

本章你将学会用 Vue Router 实现前后端分离的页面跳转，包括动态路由参数。


## 为什么要用路由？

传统的多页面网站，点击链接会向服务器请求新的 HTML 文件，页面整个刷新，有白屏闪烁。

Vue Router 实现的是 前端路由：URL 变化时不向服务器发请求，而是由 JS 动态切换显示的组件。

这样做的好处：无刷新切换页面，体验像原生 APP 一样流畅。


## Vue Router 核心概念


## 安装与配置

如果你在创建项目时已选择 Router，可以跳过安装步骤。

如果没选，终端执行：

```text
$ npm install vue-router@4
```


### 创建路由配置文件


## 实例

两种路由模式的区别：createWebHistory 产生干净的 URL（/post/1），需要服务器配置支持。如果部署环境不确定，可以用 createWebHashHistory，URL 中带 # 号（/#/post/1），无需服务器配置。


### 在 main.js 中注册路由


## 实例

RouterView 是路由系统的核心出口。

当 URL 为 / 时，它会渲染 HomeView；当 URL 为 /post/1 时，它会渲染 PostView。


## RouterLink — 声明式导航

RouterLink 是 Vue Router 提供的导航组件，替代了传统的 <a> 标签。

它不会触发页面刷新，只会通过 JS 切换显示的组件。


## 实例


## useRoute — 读取路由参数

在详情页 PostView 中，需要知道 URL 中的文章 ID 是多少，才能找到对应的文章。

useRoute 就是用来读取当前路由信息的。


## 实例

route.params.id 的值始终是字符串。即使 URL 是 /post/3，取到的也是 '3' 而非数字 3。需要数字时，用 Number(route.params.id) 或 parseInt 转换。


## 动手：完整的文章详情页

把 BlogCard 改成可点击跳转，详情页根据 ID 显示完整文章内容。


### 第一步：改造 BlogCard 支持点击跳转


## 实例


### 第二步：创建 PostView 详情页

详情页从 URL 中读取 ID，然后从文章数据中找到对应的文章显示。


## 实例

v-html 用于渲染 HTML 字符串，但要注意：不要用它渲染用户输入的内容，否则有 XSS 安全风险。这里的文章内容是开发者自己写的，所以是安全的。


## 本章小结

本章你学会了 Vue Router 的核心使用：路由表配置（path 映射到 component）、RouterLink 导航、RouterView 出口、动态路由 /post/:id、以及 useRoute 读取路由参数。

现在博客有了真正的多页面体验——首页浏览列表，点击进入详情页阅读完整内容。


## 复习重点

- 能说明 `路由跳转` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
