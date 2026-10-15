# Vue3：Vue3 简介

- 来源：[Vue3 简介](https://www.runoob.com/vue3/vue3-introduction.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3191

## 本章内容

Vue3 是一个用于构建用户界面的渐进式框架。

渐进式意味着你可以根据项目需要，只引入 Vue 的一部分能力：从一个简单的页面交互增强，到构建完整的单页应用（SPA），乃至服务端渲染（SSR）应用，Vue3 都能胜任。

Vue3 是由尤雨溪（Evan You）主导开发的渐进式 JavaScript 前端框架，于 2020 年 9 月 18 日正式发布，代号 One Piece（海贼王）。

相比 Vue2，Vue3 对核心架构进行了全面重写：响应式系统从 Object.defineProperty 升级为 Proxy，引入组合式 API（Composition API），并在性能、TypeScript 支持、包体积等方面全面提升。

Vue3 的官方定位是：一个易于上手，同时具备足够能力支撑复杂项目的框架。它既不像 Angular 那样强制要求特定架构，也不像 React 那样需要大量手动优化，而是在易用性与能力之间找到了平衡点。


### Vue3 与 Vue2 的本质区别

Vue3 不是 Vue2 的修补升级，而是一次彻底的重写。


## 核心特性

Vue3 的改进涵盖响应式系统、API 设计、编译器和新内置组件四个维度。


### 组合式 API（Composition API）

组合式 API 是 Vue3 最重要的设计变化，它解决了 Vue2 中 Options API 的根本痛点：相关逻辑分散在不同选项中，复用困难。

在 Options API 中，一个"用户搜索"功能的数据可能散落在 data、methods、computed、watch 四个选项里；而 Composition API 允许你把同一功能的所有逻辑写在一起，然后提取为可复用的函数（Composable）。


## 实例：Options API vs Composition API


## 实例：推荐写法（script setup 语法糖）

<script setup> 是组合式 API 的语法糖：它让你在 <script> 顶层直接编写组合式 API 代码，无需手动 return，所有顶层变量和函数会自动暴露给模板。这是 Vue3 目前最推荐的单文件组件写法。


### 响应式系统：Proxy 替代 defineProperty

Vue2 的响应式基于 Object.defineProperty，这个方案有两个无法根治的问题：无法监听对象新增属性、无法监听数组通过索引直接赋值。Vue3 用 Proxy 从根本上解决了这两个问题。


## 实例：ref 与 reactive


### 可组合函数（Composables）

Composables 是 Vue3 中复用有状态逻辑的标准方式，类似于 React 的自定义 Hook。

约定以 use 开头命名，把一段完整的响应式逻辑提取为独立函数，在多个组件中复用。


## 实例：自定义 Composable


## 实例：在组件中使用 Composable


### 新内置组件

Vue3 新增了三个内置组件，解决了前端开发中三类高频场景。


## 实例：Teleport 实现全局弹窗


## 实例：Suspense 处理异步组件加载


### Tree-shaking 支持

Vue3 将所有全局 API 改为具名导出（Named Export），配合 Vite / webpack 等打包工具的 Tree-shaking 能力，未使用的 API 不会被打包进最终产物。


## 实例：按需导入 API


### 生命周期钩子

Vue3 的组合式 API 对应的生命周期钩子全部以 on 开头，并在 setup 中调用。


## 实例：生命周期钩子使用


### 完整的 TypeScript 支持

Vue3 的核心库完全用 TypeScript 重写，提供精准的类型推断。配合 <script setup lang="ts">，可以直接在单文件组件中使用 TypeScript，无需额外配置。


## 实例：script setup 中使用 TypeScript


## 应用领域

Vue3 作为一个完整的前端框架生态，覆盖了从单页应用到服务端渲染、从 Web 到移动端的广泛场景。


### 单页应用（SPA）

这是 Vue3 最经典的使用场景。配合 Vue Router 4 实现前端路由，Pinia（Vue3 官方推荐的状态管理库，替代 Vuex）管理全局状态，可以构建功能完整的单页应用。

典型项目类型：企业后台管理系统、数据大屏、电商平台前台。


### 服务端渲染（SSR）与静态站点生成（SSG）

Nuxt 3 是基于 Vue3 的全栈框架，深度集成 SSR 和 SSG 能力。它自动处理服务端渲染的复杂性，让开发者像写普通 Vue 组件一样构建 SEO 友好的应用。

适用场景：内容型网站、博客、文档站、营销落地页。


### 移动端与跨平台

uni-app 支持用 Vue3 语法同时开发微信小程序、支付宝小程序、H5 和 App（iOS/Android）。Ionic + Vue3 则适合构建高质量的混合移动应用。


### 桌面端应用

Electron + Vue3（通过 electron-vite 等工具链）可以将 Vue3 应用打包为跨平台桌面程序。Tauri + Vue3 是近年流行的替代方案，用 Rust 作为后端，应用体积更小、性能更好。


## 后续章节

- UI 组件库生态
- 发展历史
- 起源（2013 - 2014）
- Vue 1.x 时代（2015）
- Vue 2.x 时代（2016 - 2020）
- Vue 3.0 发布（2020）
- 生态完善阶段（2021 - 2022）
- 持续优化阶段（2023 - 至今）
- Vue3 在三大框架中的定位
- Vue3 的局限性

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue3 简介` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
