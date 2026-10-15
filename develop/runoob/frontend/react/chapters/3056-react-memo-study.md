# React：React Memo

- 来源：[React Memo](https://www.runoob.com/react/react-memo.html)
- 分类：前端开发
- 技术：React
- 笔记类型：学习笔记
- 章节序号：3056

## 本章内容

React.memo 是一个高阶组件（Higher Order Component, HOC），用于优化函数组件的性能。它通过记忆组件的渲染输出，在组件的 props 没有变化时跳过重新渲染，从而提高性能。以下是 React.memo 的详细介绍和使用方法。


## 1. 基本使用

React.memo 的基本使用方法是将一个函数组件作为参数传递给 React.memo，并返回一个记忆化的组件。


## 实例

在这个示例中，即使 count 状态发生变化，MyComponent 也不会重新渲染，因为它的 props 没有变化。


## 2. 使用自定义比较函数

默认情况下，React.memo 只会对比前后的 props，如果没有变化则不会重新渲染。你可以通过传递一个自定义比较函数来更精确地控制重新渲染的逻辑。


### 自定义比较函数的签名：

```javascript
function areEqual(prevProps, nextProps) {
  // 返回 true 表示相等，不需要重新渲染
  // 返回 false 表示不相等，需要重新渲染
}
```


## 实例

在这个示例中，自定义比较函数检查 text 是否发生变化。如果 text 没有变化，MyComponent 不会重新渲染。


## 3. 实际应用场景

React.memo 非常适用于以下场景：

- 静态数据展示：组件接收的 props 很少变化，但组件本身较为复杂，重新渲染成本高。
- 性能优化：在大列表或表格中，每个项目都是独立的组件，使用 React.memo 可以避免不必要的重新渲染。
- 避免深度相等检查：自定义比较函数可以避免深度相等检查，特别是在 props 包含大量数据时。


## 4. 注意事项

- 浅比较：默认情况下，React.memo 进行浅比较，这意味着它只会比较 props 的一级内容，嵌套对象需要自定义比较函数。
- 状态和上下文：React.memo 只关注 props 的变化，组件内部的状态和上下文的变化不会触发重新渲染。


## 5. 与 useMemo 和 useCallback 的区别

- React.memo：用于记忆化整个组件，优化组件的渲染。
- useMemo：用于记忆化函数组件内部的值或计算结果。
- useCallback：用于记忆化函数组件内部的回调函数，避免不必要的重新创建。


## 实例

在这个示例中，useCallback 和 useMemo 用于优化函数和计算结果，React.memo 用于优化子组件的渲染。


### 小结

React.memo 是一个强大的工具，可以有效地提高函数组件的性能，避免不必要的重新渲染。通过合理使用 React.memo 和自定义比较函数，你可以在不影响应用逻辑的情况下显著优化应用性能。


## 复习重点

- 能说明 `React Memo` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
