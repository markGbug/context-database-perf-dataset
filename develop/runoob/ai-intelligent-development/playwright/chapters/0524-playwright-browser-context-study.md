# Playwright：Playwright 测试隔离与 Browser Context

- 来源：[Playwright 测试隔离](https://www.runoob.com/playwright/playwright-browser-context.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0524

## 本章内容

本章介绍 Playwright 的测试隔离机制和 Browser Context 的概念，这是保证测试稳定可靠的关键设计。


## 什么是测试隔离

测试隔离是指每个测试用例运行在完全独立的环境中，互不影响。

在 Playwright 中，每个测试自动获得一个独立的Browser Context（浏览器上下文）。


## Browser Context 是什么

Browser Context 相当于一个全新的浏览器配置文件。

创建一个 Context 就像打开一个全新的浏览器窗口，拥有自己的 Cookie、localStorage、sessionStorage，但开销极低（毫秒级）。

每个测试中的 page 和 context 都是全新的，所以一个测试修改了 localStorage 或 Cookie，不会影响其他测试。


## Context 隔离的内容

每个 Browser Context 之间完全隔离以下内容：


## 实例


## context fixture 的使用

除了 page，测试函数还可以访问 context fixture 来进行 Context 级别的操作。


## 实例


## 多 Context 场景

当你需要在同一个测试中模拟多个独立的用户时，可以手动创建 Context。


## 实例


## 测试隔离的好处


### 1. 可重现性

每个测试从相同的初始状态开始，在任何顺序下运行结果一致。


### 2. 防止级联失败

测试 A 失败不会导致测试 B 也失败，每个测试都是独立可调试的。


### 3. 支持并行执行

因为测试完全独立，Playwright 可以安全地在多个 worker 中并行运行它们。

测试隔离是 Playwright 的默认行为，每个 test() 自动获得独立的 page 和 context，无需任何额外配置。


## 复习重点

- 能说明 `Playwright 测试隔离` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
