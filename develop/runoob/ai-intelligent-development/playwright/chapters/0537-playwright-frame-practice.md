# Playwright：Playwright Frame 与新窗口

- 来源：[Playwright Frame 与新窗口](https://www.runoob.com/playwright/playwright-frame.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：练习笔记
- 章节序号：0537

## 本章内容

本章介绍如何处理 iframe、弹窗对话框、新标签页以及 Playwright 的事件系统。


## iframe 操作

Playwright 通过 frameLocator() 来定位和操作 iframe 内的元素。


### page.frameLocator() 定位 iframe


## 实例


### 获取所有 Frame


## 实例


### 嵌套 iframe

Playwright 的 frameLocator() 支持链式调用，可以深入嵌套的 iframe。


## 实例


## 弹窗处理（Dialogs）

Playwright 对浏览器原生弹窗（alert、confirm、prompt）有默认处理策略。


### 默认行为

Playwright 默认自动关闭所有弹窗：


### 自定义弹窗处理

通过 page.on('dialog') 可以拦截并自定义处理弹窗。


## 实例


### Dialog 对象方法


## 新窗口与新标签页

当点击链接或按钮打开新标签页时，Playwright 提供了多种方式来获取新页面。


### page.waitForEvent('popup') 等待弹窗


## 实例


### context.on('page') 监听新页面


## 实例


## Playwright 事件系统

Playwright 的 Page 和 Context 对象都是事件发射器，你可以监听各种事件。


### 常用页面事件


### 事件监听方法


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Playwright Frame 与新窗口` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
