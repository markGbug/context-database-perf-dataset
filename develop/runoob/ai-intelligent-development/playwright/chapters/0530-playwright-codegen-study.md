# Playwright：Playwright Codegen 测试生成器

- 来源：[Playwright Codegen](https://www.runoob.com/playwright/playwright-codegen.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0530

## 本章内容

本章介绍 Playwright 的命令行测试生成器 Codegen，通过浏览器操作自动生成测试代码。


## 什么是 Codegen

Codegen（Code Generator）是 Playwright 内置的交互式测试生成工具。

你像普通用户一样操作浏览器，Codegen 自动将你的操作转换为 Playwright 测试代码。


## 启动 Codegen

```text
# 基本用法：打开一个 URL 并开始录制
npx playwright codegen https://www.runoob.com/

# 指定代码生成的语言（默认 TypeScript）
npx playwright codegen --target=javascript https://www.runoob.com/
npx playwright codegen --target=python https://www.runoob.com/
```

启动后会打开两个窗口：

- 浏览器窗口：你在这个窗口中操作页面
- Playwright Inspector 窗口：实时显示生成的代码


## 录制操作

在浏览器窗口中进行任何操作，Codegen 都会自动生成对应的 Playwright 代码：


### 导航

在地址栏输入新的 URL 并回车，会生成 page.goto() 语句。


### 点击

点击任意元素（按钮、链接、菜单），会生成 page.getByRole(...).click() 或类似的定位+点击代码。


### 输入

在输入框中输入文字，会生成 page.getByLabel(...).fill(...) 或 page.getByPlaceholder(...).fill(...)。


### 选择

在下拉菜单中选择选项，会生成 page.getByLabel(...).selectOption(...)。


### 复选框

勾选或取消勾选复选框，会生成 page.getByLabel(...).check() 或 .uncheck()。


## 自动选择最佳 Locator

Codegen 会分析页面元素的属性，按以下优先级生成 Locator：

- getByRole() —— 元素具有明确的 ARIA 角色
- getByText() —— 元素有明确文本内容
- getByLabel() —— 表单元素有 label 关联
- getByPlaceholder() —— 输入框有 placeholder
- getByAltText() —— 图片有 alt 属性
- getByTestId() —— 元素有 data-testid
- getByTitle() —— 元素有 title 属性
- locator() —— CSS 选择器（最后选择）

如果 Codegen 找到多个匹配元素，它会自动优化 Locator，直到能唯一确定目标元素。


## 生成断言

在 Inspector 窗口的工具栏中，可以点击断言按钮来生成断言代码：

- Assert Visibility —— 点击后选中元素，生成 await expect(locator).toBeVisible()
- Assert Text —— 生成 await expect(locator).toHaveText(...)
- Assert Value —— 生成 await expect(locator).toHaveValue(...)
- Assert Snapshot —— 生成 await expect(locator).toHaveScreenshot()


## 常用 Codegen 选项


## Codegen vs VS Code 录制的选择


## 复习重点

- 能说明 `Playwright Codegen` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
