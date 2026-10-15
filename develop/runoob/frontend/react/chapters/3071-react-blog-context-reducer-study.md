# React：全局状态 — Context + useReducer

- 来源：[全局状态](https://www.runoob.com/react/react-blog-context-reducer.html)
- 分类：前端开发
- 技术：React
- 笔记类型：学习笔记
- 章节序号：3071

## 本章内容

本章你将学会用 React Context + useReducer 管理跨组件、跨页面的共享数据，并实现「收藏文章」功能。


## 为什么需要全局状态？

到目前为止，数据通过 Props 层层传递。但有些数据需要被多个不相关的组件访问：

- 收藏列表需要在首页、详情页、导航栏之间共享
- 用户登录状态所有页面都要知道
- 购物车数据需要跨页面访问

Props 逐层传递（Prop Drilling） 的痛点：A → B → C → D，中间组件被迫接收自己不用的 Props。

Context 提供了一个全局的「数据通道」，任何子孙组件都可以直接读取，跳过中间层。


## Context 的核心概念


## createContext 与 Provider


## 实例

Context 就像一个「广播塔」：Provider 往外广播数据，useContext 接收数据。


## useReducer — 管理复杂状态

当状态逻辑变得复杂（多个子状态、多种更新方式），useState 就捉襟见肘了。

useReducer 提供了类似 Redux 的状态管理模式：dispatch action → reducer 计算新状态。


## 实例


### useState vs useReducer


## Context + useReducer 组合模式

这是 React 中最强大的全局状态管理方案，也是 Redux 的核心思想。


## 实例


### 在 main.jsx 中注册 Provider


## 实例

为什么要把 Provider 放在 RouterProvider 外面？因为导航栏 NavBar（在 App 中）也需要读取收藏状态。Provider 必须包裹所有需要访问这个状态的组件。


## 在组件中使用收藏功能


### BlogCard 中的收藏按钮


## 实例


### PostPage 中的收藏按钮


## 实例


### NavBar 中显示收藏数量


## 实例

首页收藏一篇文章后，进入详情页自动显示「已收藏」，导航栏的数字也同步更新——这就是 Context 全局共享的价值。


## Context + useReducer vs Vue3 Pinia


## 本章小结

本章你掌握了 React 全局状态管理的完整方案：createContext 创建容器、Provider 注入数据、useContext 消费数据、useReducer 管理复杂更新逻辑。

「收藏文章」功能让首页、详情页、导航栏的数据保持全局同步，刷新页面后也能通过 localStorage 恢复。


## 复习重点

- 能说明 `全局状态` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
