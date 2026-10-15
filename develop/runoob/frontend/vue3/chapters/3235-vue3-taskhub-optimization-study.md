# Vue3：逻辑复用与性能优化

- 来源：[逻辑复用与性能优化](https://www.runoob.com/vue3/vue3-taskhub-optimization.html)
- 分类：前端开发
- 技术：Vue3
- 笔记类型：学习笔记
- 章节序号：3235

## 本章内容

在完成路由与登录逻辑后，随着项目规模扩大，我们会发现有些逻辑（如存取本地数据、弹出通知）在多个页面反复出现。同时，如果任务列表达到上千条，页面可能会出现卡顿。

这一阶段，我们将通过 Composition API 的深度应用 来解决代码复用和性能瓶颈问题。


## 逻辑复用：自定义 Composables (Hooks)

Composables 是 Vue 3 的精髓，它允许我们将逻辑（State + Actions）抽离成独立函数。


### useLocalStorage：数据持久化逻辑抽离

不再在每个 Store 或组件里手写 localStorage.getItem。


## 实例


### useNotification：公共 UI 逻辑抽离

实现一个简单的通知提示功能。


## 实例


## 性能调优：处理大数据量与高频渲染

当你的 TaskHub 从管理 10 个任务增长到管理 1000 个任务时，Vue 默认的"深度响应式"会带来计算压力。


### shallowRef 与 markRaw

Vue 默认的 ref 是递归响应式的（即对象内部的每个属性都会被代理）。

shallowRef：只监听 .value 的指向变化，不监听对象内部属性的变化。

- 场景：当你从后端获取一大串只读的任务历史记录时。

markRaw：标记一个对象，使其永远不会被转为响应式。

- 场景：某些复杂的第三方库实例（如 ECharts 图表实例、地图实例），包装成响应式反而会报错或极度耗费性能。

```javascript
// 性能优化示例
import { shallowRef, markRaw } from 'vue';

// 假设这是一万条历史归档数据
const archiveTasks = shallowRef([]);

const loadArchive = (data) => {
  // 仅在赋值时触发一次响应式更新，内部属性修改不触发
  archiveTasks.value = data;
};
```


### v-once 与 v-memo (指令级优化)

如果某个任务渲染后就不再变化（比如任务的创建时间），使用 v-once。

```html
<span v-once>创建于: {{ task.createdAt }}</span>
```

- 原理：Vue 渲染后会跳过该节点的后续更新检查。

这是优化长列表最强大的指令。它接受一个依赖数组，只有当数组里的值变化时，该节点及其子节点才会重新渲染。

```html
<li v-for="task in tasks" :key="task.id" v-memo="[task.isCompleted, task.title]">
  {{ task.title }} - {{ task.isCompleted }}
</li>
```


## 什么时候该调优？


## 结合到之前的项目中

你可以尝试在 TaskItem.vue 中应用 v-memo：

```html
<template>
  <li v-memo="[task.id, task.isCompleted]" class="...">
     ...
  </li>
</template>
```

现在你的项目不仅逻辑清晰（Composables），而且性能强劲。


## 复习重点

- 能说明 `逻辑复用与性能优化` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
