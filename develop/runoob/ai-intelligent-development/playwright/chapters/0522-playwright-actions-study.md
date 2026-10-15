# Playwright：Playwright 操作（Actions）

- 来源：[Playwright 操作](https://www.runoob.com/playwright/playwright-actions.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0522

## 本章内容

本章介绍 Playwright 中与导航和点击相关的操作，以及操作背后的自动等待机制。


## 什么是 Action

Action（操作）是 Playwright 中用来模拟用户行为的方法，比如点击按钮、输入文字、选择下拉框。

每个 Action 在执行之前，Playwright 会自动等待目标元素变为可操作状态。


## Actionability 可操作性检查

在执行每个操作前，Playwright 会对目标元素进行一系列检查：

任意一步未通过，Playwright 都会等待并重试，直到超时。

这 5 步检查是 Playwright 自动完成的，你不需要写任何额外的等待代码。这也是 Playwright 能够大幅减少不稳定测试的根本原因。


## 强制操作 { force: true }

有时你需要绕过可操作性检查，例如点击一个被遮罩隐藏的按钮或测试不可见元素的状态。


## 实例

force: true 是测试真实用户做不到的操作，绝大多数情况下不应使用。如果你的测试需要 force: true，先检查是否有交互设计问题。


## 导航操作


### page.goto() 页面跳转


## 实例


### page.goBack() / goForward() / reload()


## 实例


## 点击操作


### locator.click() 单击


## 实例


### locator.dblclick() 双击


## 实例


### 右键点击


## 实例


### 组合键点击


## 实例


### 坐标点击


## 实例


### locator.hover() 悬停


## 实例


## 点击 vs hover 的场景差异


## 文本输入操作


## 后续章节

- locator.fill() 清空后填入
- 实例
- locator.type() 逐字输入
- 实例
- fill vs type 的区别
- locator.clear() 清空
- 实例
- 选择操作
- locator.check() / uncheck() 复选框
- 实例
- locator.selectOption() 下拉框选择
- 实例
- 键盘操作
- page.keyboard.press() 按键
- 实例
- page.keyboard.down() / up() 按下/松开

## 复习重点

- 能说明 `Playwright 操作` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
