# Playwright：Playwright 自动等待与超时

- 来源：[Playwright 等待与超时](https://www.runoob.com/playwright/playwright-waiting-timeout.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：练习笔记
- 章节序号：0523

## 本章内容

本章深入介绍 Playwright 的自动等待机制，以及手动等待和超时配置的完整知识。


## 为什么需要自动等待

现代 Web 应用大量使用异步渲染，页面内容不会瞬间全部加载完毕。

传统测试框架中，开发者不得不写 sleep 或 waitFor 来等待，但这些操作不够灵活，要么等待太久拖慢测试，要么等待不够导致 flaky。

Playwright 将等待逻辑内置到每个 Locator 和 Action 中，从根本上解决这个问题。


## 三层自动等待体系


### 第一层：Locator 的自动等待

当你创建 Locator 时，Playwright 不立即查找元素，而是在你执行操作或断言时才开始查找并自动等待。


## 实例


### 第二层：Action 的可操作性检查

在执行操作（click、fill 等）前，Playwright 确保元素：Attached → Visible → Stable → Receives Events → Enabled。


### 第三层：Assertion 的自动重试

断言失败后不会立即报错，而是持续重试直到条件满足或超时。


## 实例


## 手动等待方法

在自动等待不够用的特殊场景下，Playwright 也提供了手动等待方法。


### page.waitForTimeout(ms) ——固定等待


## 实例

尽量避免使用 waitForTimeout，固定等待在设备性能差异下极不稳定。优先使用后文的 waitForURL、waitForResponse 等事件驱动等待。


### page.waitForURL() ——等待 URL 变化


## 实例


### page.waitForLoadState() ——等待加载状态


## 实例


### page.waitForResponse() ——等待网络响应


## 实例


### page.waitForEvent() ——等待事件


## 实例


## 超时配置详解

Playwright 有 4 种超时类型，分别作用于不同层面：


### 全局配置


## 实例


### 单次设置（优先级高于全局配置）


## 实例


### 超时优先级

单次设置 > 配置文件全局设置 > 默认值。


## 后续章节

- 合理设置超时的建议

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Playwright 等待与超时` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
