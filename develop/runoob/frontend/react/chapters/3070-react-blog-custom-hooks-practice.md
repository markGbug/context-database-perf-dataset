# React：自定义 Hook — 封装可复用逻辑

- 来源：[自定义 Hook](https://www.runoob.com/react/react-blog-custom-hooks.html)
- 分类：前端开发
- 技术：React
- 笔记类型：练习笔记
- 章节序号：3070

## 本章内容

本章你将学会 React 最佳实践——用自定义 Hook 封装可复用的逻辑，让组件更简洁、更易维护。


## 什么是自定义 Hook？

随着功能增多，useState 和 useEffect 散落在组件中，不同组件间有重复逻辑。

自定义 Hook 就是把多个 Hook 的组合逻辑提取到一个以 use 开头的函数中。

它的本质：一个内部使用了 React Hook 的普通 JS 函数。


## 为什么需要自定义 Hook？


## 命名规范与 Hook 规则

Hook 的使用规则：1. 只在函数组件顶层调用 Hook；2. 只在 React 函数中调用 Hook（函数组件或自定义 Hook）。这确保了每次渲染时 Hook 的调用顺序一致。


## usePosts — 封装文章数据逻辑


## 实例


### 使用 usePosts 的首页


## 实例


### 使用 usePosts 的详情页


## 实例

注意：如果用户直接访问详情页 URL（如刷新页面），usePosts 会重新 fetch 数据。这是正确的行为——因为首页的 usePosts 实例和详情页的 usePosts 实例是独立的，各自调用自己的 useEffect。


## useDarkMode — 一行代码切换暗黑模式


## 实例

在 NavBar 中使用：


## 实例


### CSS 变量实现主题切换


## 实例


## React 自定义 Hook vs Vue3 Composable


## 本章小结

本章你掌握了 React 最重要的设计模式——自定义 Hook：以 use 开头、内部组合多个 React Hook、返回状态和操作。

usePosts 统一管理数据加载 + 筛选 + 搜索，useDarkMode 实现一行代码接入暗黑模式。组件从此只关心 UI 渲染。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `自定义 Hook` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
