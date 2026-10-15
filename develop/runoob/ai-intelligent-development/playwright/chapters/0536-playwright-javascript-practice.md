# Playwright：Playwright JavaScript 执行

- 来源：[Playwright JavaScript 执行](https://www.runoob.com/playwright/playwright-javascript.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：练习笔记
- 章节序号：0536

## 本章内容

本章介绍如何在 Playwright 中执行 JavaScript 代码，包括页面上下文执行、参数传递和初始化脚本注入。


## page.evaluate() 页面上下文执行

page.evaluate() 在页面的 JavaScript 环境中执行代码，可以访问 DOM 和页面全局变量。


## 实例


## 向 evaluate 传递参数

page.evaluate() 的第二个参数会传递给页面内的函数。


## 实例

传递的参数会被 JSON 序列化后发送到页面上下文，因此不能传递函数、DOM 元素等无法序列化的对象。

传回的值同样会被序列化。


## locator.evaluate() 元素上下文执行

locator.evaluate() 在匹配的元素上下文中执行代码，参数中包含该元素的 DOM 节点引用。


## 实例


## locator.evaluateAll() 遍历所有匹配元素

evaluateAll() 对所有匹配元素执行相同的代码，返回数组。


## 实例


## page.addInitScript() 注入初始脚本

addInitScript() 在页面加载之前注入 JavaScript 代码，可以在页面脚本执行前修改浏览器环境。


## 实例

addInitScript() 常见用途：


## ElementHandle 的用途与局限

ElementHandle 是 DOM 元素的直接引用，在 Playwright 早期版本中广泛使用。

现在大多数场景应使用 Locator 替代 ElementHandle。


## 实例

ElementHandle 仅在需要获取 boundingBox() 或进行复杂 DOM 操作时使用。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Playwright JavaScript 执行` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
