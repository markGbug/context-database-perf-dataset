# Playwright：Playwright 定位器（Locators）

- 来源：[Playwright 定位器](https://www.runoob.com/playwright/playwright-locators.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0520

## 本章内容

Locator（定位器）是 Playwright 中最核心的概念之一，它代表了一种在页面上查找元素的方式。

本章介绍 Playwright 推荐的定位方法：通过角色、文本、标签和占位符来定位元素。


## 什么是 Locator

Locator 是 Playwright 用来在页面上查找元素的抽象对象。

与传统的 document.querySelector() 不同，Playwright 的 Locator 具有自动等待和自动重试能力。

当页面内容动态变化时，Locator 会不断重新查找元素，直到找到匹配的元素或超时。


## 实例


### Locator 的工作原理

创建 Locator 时，Playwright 只记录了一个查找规则。

当你调用 .click()、.fill() 等操作或 expect(locator) 断言时，Locator 才真正开始查找元素。

如果找不到元素，Locator 会持续重试，直到操作超时为止。


## 按角色定位：getByRole()

getByRole() 是 Playwright 最推荐的定位方式。

它通过元素的可访问性角色（ARIA Role）来查找元素，这是最接近用户感知的方式。


### 基本用法


## 实例


### 常见 ARIA Role


### name 选项

name 选项是通过元素的可访问名称来缩小范围。

可访问名称的来源包括：元素文本内容、aria-label 属性、关联的 <label> 等。


## 实例


### 状态选项

除了 name，getByRole 还支持多种状态选项：


## 实例


## 按文本定位：getByText()

getByText() 通过元素的文本内容来定位。


## 实例

getByText 匹配的是元素的完整文本内容，所以 getByText('RUNOOB', { exact: true }) 只会匹配文本内容刚好为 "RUNOOB" 的元素。

默认不做精确匹配时，子字符串匹配即可（如 getByText('RUNOOB') 会匹配 "欢迎访问 RUNOOB"）。


## 按标签定位：getByLabel()

getByLabel() 用于定位与 <label> 关联的表单控件。


## 实例

它也支持 { exact: true } 精确匹配选项。


## 按占位符定位：getByPlaceholder()

getByPlaceholder() 通过 placeholder 属性定位输入框。


## 实例


### getByLabel vs getByPlaceholder 的选择

getByRole 是 Playwright 最推荐的定位方式，因为它模拟用户通过角色识别元素的方式。其次是 getByLabel 和 getByPlaceholder。在没有语义化元素的情况下才考虑使用 getByTestId 或 CSS 选择器。


## getByAltText() 图片定位

getByAltText() 通过图片的 alt 属性来定位 <img> 元素。


## 实例


## getByTitle() 标题属性定位

getByTitle() 通过元素的 title 属性来定位。


## 实例

getByAltText 和 getByTitle 使用频率较低，仅在元素具有明确的 alt 或 title 属性且无法用其他方式定位时才使用。


## getByTestId() 测试 ID 定位

getByTestId() 是兜底方案，通过 data-testid 属性来定位元素。


## 实例


## 后续章节

- 自定义 testId 属性
- 实例
- page.locator() CSS 与 XPath 定位
- CSS 选择器
- 实例
- XPath 定位
- 实例
- Locator 链式操作
- .first()、.last()、.nth()
- 实例
- .filter() 过滤
- 实例
- .locator() 子元素定位
- 实例
- .and() 和 .or() 逻辑组合（1.63+）
- 实例

## 复习重点

- 能说明 `Playwright 定位器` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
