# Vue3：路由系统

- 来源：[路由系统](https://www.runoob.com/vue3/vue3-taskhub-router.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：学习笔记
- 章节序号：3234

## 本章内容

上一章节我们的任务管理逻辑已经通过 Pinia 实现了持久化，现在我们需要为应用注入灵魂——路由系统。

在企业级开发中，路由不只是切换页面，更承担了安全性（权限控制）和用户体验（动态标题）的重任。


## 安装与基础配置

首先安装 Vue Router：

```text
npm install vue-router
```

在 src 目录下创建 router 目录，并创建 router/index.js 文件。

我们将定义两个页面：工作台 (Dashboard) 和 登录页 (Login)。


## 实例

在 src 下创建 views 文件夹，并分配好页面。

- src/App.vue：根容器，只放 <router-view /> 和全局动画。
- src/views/Dashboard.vue：原本的 TaskHub 核心功能（任务列表、输入框等）。
- src/views/Login.vue：新增的登录页面。


### 改造 App.vue (变成干净的容器)


## 实例


### 把原本的逻辑迁入 Dashboard.vue

把之前在 App.vue 里写的那些代码（引入 Store、引入组件、模板布局）全部剪切到 src/views/Dashboard.vue 中。


## Dashboard.vue 文件代码


### 登录逻辑实现 (Login.vue)

利用 Tailwind v4 快速构建一个极简登录页，并模拟登录行为。


## 实例


### 完善 router/index.js 的拦截逻辑

确保你的路由配置中已经开启了安检模式：


## 实例


### 在 main.js 中完成最后拼图

确保你的 main.js 引入并挂载了路由：


## 实例


### 最终效果

- 访问 /：如果你没登录，页面会闪现一下然后跳转到/login。
- 访问 /login：点击按钮，本地存储isLoggedIn变为true，然后瞬间切入工作台。
- 刷新页面：Pinia 会从 LocalStorage 读取任务，路由守卫会检查登录状态，一切数据都不会丢失。

登录后，可以点击退出登录：


### 知识点讲解

- 为什么 App.vue 变空了？ 在单页面应用（SPA）中，App.vue 是整个应用的外壳。我们把它变空是为了能根据 URL 的变化，在其中动态地塞进不同的页面（Dashboard 或 Login）。
- useRouter 的实战： 在 Dashboard.vue 中，我们通过 router.push('/login') 实现了退出功能。注意：push 会向浏览器历史记录添加一条新记录，点击浏览器返回键是可以回退的。
- Tailwind v4 的布局继承： 由于我们在 App.vue 的全局容器里加了 bg-slate-50 和 min-h-screen，所有的子页面（Dashboard、Login）都会默认继承这个浅灰色背景，保证了视觉的统一性。


## 复习重点

- 能说明 `路由系统` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
