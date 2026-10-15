# Vue3：Pinia 入门教程

- 来源：[Vue3 Pinia](https://www.runoob.com/vue3/vue3-pinia.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：练习笔记
- 章节序号：3218

## 本章内容

在 Vue3 中，状态管理是一个绕不开的话题。

Pinia 是 Vue.js 的轻量级状态管理库，它让你能够在组件之间共享和管理状态，我们可以把 Pinia 想象成一个全局的数据仓库，所有组件都可以从这里获取数据或者更新数据。

本章节我们要介绍的是 Vue3 官方推荐的状态管理库 —— Pinia，相比 Vuex，Pinia 提供了更简洁、更符合 Vue3 组合式 API 思维的状态管理方案。

下图对比了两者的结构差异：

- Vuex 采用单仓库加多级模块的树状结构，层级固定，依赖 mutations，整体更重。
- Pinia 则由多个独立 store 组成，扁平、轻量、不分模块，无命名空间负担。

Pinia 核心特点：

- 支持 Vue2 和 Vue3
- 极简的 API 设计
- 完整的 TypeScript 支持
- 支持组合式 API
- 模块化设计，无需嵌套模块

Pinia 的扁平结构让组件可以直接连到任意 store，各取所需，不经过树状模块，也不走命名空间路径，状态流动简单直接，耦合度低。


## 安装与配置

用 Vite 创建项目：

```text
npm create vite@latest vue-pinia-demo --template vue
cd vue-pinia-demo
npm install
```


### 安装 Pinia

首先，在你的 Vue3 项目中安装 Pinia：

```text
npm install pinia
# 或者
yarn add pinia
```

Pinia 有三部分：

- state：存数据
- getters：算派生数据
- actions：执行逻辑、修改 state


### 配置 Pinia

在 src/main.js 或 src/main.ts 中配置 Pinia：


## 实例


## 创建第一个 Store

Store 就是 Pinia 中的数据仓库，我们来创建一个简单的计数器 Store。


### 定义 Store

新建 src/stores/useCounter.js：


## 实例


### Store 的结构说明

让我们通过一个表格来理解 Store 的各个部分：


## 在组件中使用 Store


### 基本使用

src/components/CounterComponent.vue 组件代码如下：


## 实例

修改 src/App.vue 代码如下：


## 实例

整个项目结构： 执行 npm run dev 命令，在浏览器访问 http://localhost:5173/，查看效果：


### 响应式解构

如果你想在模板中直接使用 state 的属性，可以使用 storeToRefs：


## 实例


## 组合式 API 风格的 Store

Pinia 也支持使用组合式 API 的风格来定义 Store：


## 实例


## Store 之间的交互

多个 Store 之间可以相互调用：


## 实例


## 实际应用示例：购物车

让我们创建一个完整的购物车示例：


## 实例


## 实例


### 在组件中使用购物车


## 实例


## 最佳实践和注意事项


## 后续章节

- 1. Store 命名规范
- 实例
- 2. 状态初始化
- 实例
- 3. 异步操作处理
- 实例
- 4. 数据持久化
- 实例
- Pinia API

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Vue3 Pinia` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
