# React：响应式数据 — useState

- 来源：[响应式数据](https://www.runoob.com/react/react-blog-usestate.html)
- 分类：前端开发
- 技术：React
- 笔记类型：学习笔记
- 章节序号：3065

## 本章内容

useState 是 React 最重要的 Hook。本章你将理解 React 的状态管理机制，并实现分类筛选功能。


## React 的「响应式」与 Vue3 有何不同？

Vue3 用 ref/reactive 创建响应式数据，数据变了视图自动更新。

React 的思路不同：当你修改 state，React 会用新的 state 重新执行一遍组件函数，渲染出新的视图。

这就是 React 名字的由来——组件对 state 的变化做出「反应」。


## useState 基本用法

useState 是 React 最基础的 Hook，用来给函数组件添加状态。


## 实例

每次点击按钮，setCount 更新 count 的值，React 用新值重新执行 Counter 函数，返回新的 JSX，页面自动更新。

React 的约定：状态名用 [something, setSomething] 解构。set 开头的函数是约定俗成的命名规范，不是硬性要求，但全社区都这么写。


## 为什么不能直接修改 state？

在 React 中，state 是只读的。必须通过 setter 函数更新，不能直接改。


## 实例

这背后是 React 的 不可变（Immutable） 原则：不修改旧数据，而是用新数据替换。


## 更新数组和对象的正确姿势

对于数组和对象，不能直接 push、splice 或修改属性，必须创建新副本。


## 实例

核心原则：永远用新数组/新对象替换旧的。展开运算符 ... 和你学过的数组方法（map、filter）是不变性更新的最佳搭档。


## useMemo — 派生计算值

useMemo 用于缓存计算结果。依赖没变时跳过重新计算，避免不必要的性能开销。


## 实例

useMemo(fn, deps) 的依赖数组要填完整：函数里用到的所有组件内部变量都应在数组中声明。React 通过浅比较来决定是否重新计算。


## 动手：给博客加上分类筛选


## 实例


## 实例


## 本章小结

本章你掌握了 React 状态管理的三个核心概念：useState 创建和更新状态、不可变更新原则（展开运算符 + map/filter）、useMemo 缓存派生计算值。

通过分类筛选功能，你体验了 React「setState → 重新渲染 → 新视图」的数据驱动模式。


## 复习重点

- 能说明 `响应式数据` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
