# React：副作用与数据请求 — useEffect

- 来源：[副作用与数据请求](https://www.runoob.com/react/react-blog-useeffect.html)
- 分类：前端开发
- 技术：React
- 笔记类型：练习笔记
- 章节序号：3068

## 本章内容

本章你将学会 React 最重要的副作用 Hook——useEffect，并在恰当的时机用 fetch 从 JSON 文件加载博客数据。


## 什么是副作用？

在 React 中，副作用（Side Effect） 指的是那些与渲染无关的操作：

- 向服务器请求数据
- 操作 localStorage
- 设置定时器 setInterval
- 手动修改 DOM
- 订阅外部事件

副作用不能在组件函数体里直接执行（会导致每次渲染都执行），必须放在 useEffect 中。


## useEffect 基本用法


## 实例


### 依赖数组的三种写法

省略依赖数组 vs 空数组的区别：useEffect(fn) 每次渲染后都执行；useEffect(fn, []) 只在首次渲染后执行一次。前者极易造成死循环（effect 中 setState → 触发渲染 → 再执行 effect → ...），几乎从来不用。


## 用 fetch 加载 JSON 数据

与 Vue3 一样，我们把文章数据放到 public/posts.json 文件中。


### 第一步：创建数据文件


## 实例


### 第二步：在 useEffect 中加载数据


## 实例

cancelled 标记是 React 中的常见模式。当 fetch 还在进行中时，如果用户离开页面（组件卸载），后续的 setState 会报错警告。cleanup 函数中设置 cancelled = true 可以在卸载后跳过 setState。


## 清理函数（Cleanup）

useEffect 的回调函数可以返回一个函数，称为 清理函数。

它在两个时机执行：组件卸载时 和 下一次 effect 执行前。


## 实例


## 处理异步请求的四种状态

任何数据请求都应覆盖以下四种 UI 状态：


## VS Vue3 生命周期对照


## 本章小结

本章你掌握了 useEffect 的核心用法：依赖数组的三种写法、用 fetch 异步加载数据、四种 UI 状态处理、以及 cleanup 清理函数的作用。

现在博客数据从外部 JSON 动态加载，不再硬编码在 JS 中。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `副作用与数据请求` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
