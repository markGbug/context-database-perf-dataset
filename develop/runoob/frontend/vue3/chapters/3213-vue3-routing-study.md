# Vue3：Vue3 路由(Vue Router)

- 来源：[Vue3 路由](https://www.runoob.com/vue3/vue3-routing.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：学习笔记
- 章节序号：3213

## 本章内容

本章节我们将为大家介绍 Vue 路由。

Vue 路由允许我们通过不同的 URL 访问不同的内容。

通过 Vue 可以实现多视图的单页 Web 应用（single page web application，SPA）。

Vue.js 路由需要载入 vue-router 库

中文文档地址：vue-router 文档。

Vue Router 负责将 URL 路径与应用中的组件进行映射，当用户在应用中浏览时，URL 会更新，但页面不会重新加载，从而提供流畅的用户体验。

上图展示了一个两层级的嵌套路由结构：

- 顶层 (App.vue 的 <router-view>) 负责渲染独立布局（如 Login.vue）或主框架布局（Layout.vue）。
- 主框架布局 (Layout.vue) 内部包含第二个 <router-view>，用于渲染功能页面的子组件（如 Dashboard.vue、User.vue），从而实现页头、侧边栏和页脚的持久化显示。
- 未匹配的路径最终会导向独立的 page404.vue。


### 核心组成部分


## 安装


### npm 安装

```text
npm install vue-router
```


### npm（国内镜像）

推荐使用淘宝镜像：

```text
npm install -g cnpm --registry=https://registry.npmmirror.com
cnpm install vue-router@4
```


### 直接下载 / CDN

```text
https://unpkg.com/vue-router@4
```


### 基本应用


### 1、创建路由表

```javascript
// src/router/index.js
import { createRouter, createWebHistory } from 'vue-router'
import Home from '../views/Home.vue'
import About from '../views/About.vue'

const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About }
]

export default createRouter({
  history: createWebHistory(),
  routes
})
```


### 2、在应用中挂载

```text
// main.js
import { createApp } from 'vue'
import App from './App.vue'
import router from './router'

createApp(App).use(router).mount('#app')
```


### 3、页面出口

```html
<router-view></router-view>
```


### 4、跳转

```html
<router-link to="/about">About</router-link>
```


### 5、动态路由

```text
{ path: '/user/:id', component: User }
```

访问 /user/10，$route.params.id === '10'。


### 6、懒加载

```javascript
const About = () => import('../views/About.vue')
```


### 7、导航守卫（鉴权）

```text
router.beforeEach((to, from, next) => {
  next()
})
```


### 8、重定向

```text
{ path: '/old', redirect: '/' }
```


### 9、404

```text
{ path: '/:pathMatch(.*)*', component: NotFound }
```


## 简单实例

Vue.js + vue-router 可以很简单的实现单页应用。

<router-link> 是一个组件，该组件用于设置一个导航链接，切换不同 HTML 内容。 to 属性为目标地址， 即要显示的内容。

以下实例中我们将 vue-router 加进来，然后配置组件和路由映射，再告诉 vue-router 在哪里渲染它们。代码如下所示：


## HTML 代码

```html
<div id="app">
  <h1>Hello App!</h1>
  <p>
    <!--使用 router-link 组件进行导航 -->
    <!--通过传递 `to` 来指定链接 -->
    <!--`<router-link>` 将呈现一个带有正确 `href` 属性的 `<a>` 标签-->
    <router-link to="/">Go to Home</router-link>
    <router-link to="/about">Go to About</router-link>
  </p>
  <!-- 路由出口 -->
  <!-- 路由匹配到的组件将渲染在这里 -->
  <router-view></router-view>
</div>
```


### router-link

请注意，我们没有使用常规的 a 标签，而是使用一个自定义组件 router-link 来创建链接。这使得 Vue Router 可以在不重新加载页面的情况下更改 URL，处理 URL 的生成以及编码。我们将在后面看到如何从这些功能中获益。


### router-view

router-view 将显示与 url 对应的组件。你可以把它放在任何地方，以适应你的布局。


## JavaScript 代码

```html
// 1. 定义路由组件.
// 也可以从其他文件导入
const Home = { template: '<div>Home</div>' }
const About = { template: '<div>About</div>' }

// 2. 定义一些路由
// 每个路由都需要映射到一个组件。
// 我们后面再讨论嵌套路由。
const routes = [
  { path: '/', component: Home },
  { path: '/about', component: About },
]

// 3. 创建路由实例并传递 `routes` 配置
// 你可以在这里输入更多的配置，但我们在这里
// 暂时保持简单
const router = VueRouter.createRouter({
  // 4. 内部提供了 history 模式的实现。为了简单起见，我们在这里使用 hash 模式。
  history: VueRouter.createWebHashHistory(),
  routes, // `routes: routes` 的缩写
})

// 5. 创建并挂载根实例
const app = Vue.createApp({})
//确保 _use_ 路由实例使
//整个应用支持路由。
app.use(router)

app.mount('#app')

// 现在，应用已经启动了！
```

点击过的导航链接都会加上样式 class ="router-link-exact-active router-link-active"。


### 应用实例

以下例子涵盖了路由的定义、创建、挂载、导航和渲染五个核心步骤。

1. main.js (入口文件)


## 实例

2. router/index.js (路由配置)


## 实例

3. App.vue (根组件)


## 实例

当您运行此应用时：

- 点击 Home 链接，URL 变为 /，<router-view> 中显示 Home Page 组件内容。
- 点击 About 链接，URL 变为 /about，<router-view> 中显示 About Us 组件内容。
- 点击 404 Demo 链接，URL 变为 /nonexistent，<router-view> 中显示 404 Not Found 组件内容。


## 后续章节

- <router-link> 相关属性
- to
- replace
- append
- tag
- active-class
- exact-active-class
- event
- Vue Router (v4, Vue 3) 核心 API 手册
- 一、createRouter 配置项
- 二、History 工厂
- 三、RouteRecord (路由表项)
- 四、路由导航 (Router 实例方法)
- 五、导航守卫
- 六、<router-link> 属性
- 七、<router-view> 属性

## 复习重点

- 能说明 `Vue3 路由` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
