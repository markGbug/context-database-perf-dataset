# Playwright：Playwright 页面操作基础

- 来源：[Playwright 页面操作基础](https://www.runoob.com/playwright/playwright-page-operation-basics.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：练习笔记
- 章节序号：0512

## 本章内容

本章节我们来了解下 Playwright 如何与网页进行实际交互及最常用的页面操作 API。


## 页面导航

页面导航是最常见的操作，Playwright 提供了多个 API 来打开、刷新和控制页面的跳转。


### 1. 打开网页（page.goto）

```text
await page.goto('https://example.com');
```

常用参数：

- url：要访问的地址
- timeout：超时时间，默认 30 秒
- waitUntil：等待页面加载的条件 'load'：等待 load 事件（页面和资源全部加载完） 'domcontentloaded'：等待 DOM 内容加载完 'networkidle'：等待网络空闲


## 实例


### 2. 页面刷新（page.reload）

刷新当前页面。

```text
await page.reload({ waitUntil: 'networkidle' });
```


### 3. 前进 / 后退（page.goBack / page.goForward）

模拟浏览器的前进、后退按钮。

```text
await page.goto('https://example.com');
await page.goto('https://playwright.dev');

await page.goBack();   // 返回 example.com
await page.goForward(); // 前进到 playwright.dev
```


### 4. 等待页面加载

有时需要显式等待页面加载某个元素，Playwright 提供了智能等待机制。

```text
await page.waitForLoadState('networkidle'); // 等待网络空闲
await page.waitForSelector('#main-content'); // 等待元素出现
```


## 元素定位

要与页面交互，首先要定位到目标元素。Playwright 提供了多种选择器。


### 1. CSS 选择器

最常用的定位方式，和前端开发一致。

```text
await page.click('#login-button');     // 通过 id
await page.click('.btn-primary');      // 通过 class
await page.click('form > button');     // 通过层级关系
```


### 2. XPath 选择器

通过 XPath 表达式定位元素。

```text
await page.click('//button[text()="登录"]');
await page.click('//input[@name="username"]');
```

XPath 更灵活，但可读性较差，不推荐作为首选。


### 3. 文本内容定位

通过元素的可见文本进行定位。

```text
await page.click('text=登录');
await page.click('button:has-text("提交")');
```


### 4. 属性定位

直接使用属性来选择。

```text
await page.fill('input[name="email"]', 'test@example.com');
await page.click('[data-test="submit-button"]');
```


### 5. 定位策略最佳实践

- 优先使用唯一且稳定的选择器（如 data-testid、data-test 属性）
- 避免依赖动态的 id 或 class 名
- 使用 page.getByRole、page.getByText 等可读性更好的方法（Playwright 5.x 推荐）


## 实例


## 基础交互

Playwright 支持多种与元素交互的方式，涵盖点击、输入、键盘和鼠标操作。


### 1. 点击操作（page.click）

```text
await page.click('#submit');
```

可选参数：

- button：'left' | 'right' | 'middle'（默认左键）
- clickCount：点击次数（双击时设为 2）
- modifiers：键盘组合键（如 ['Control']）


## 实例


### 2. 输入文本（fill vs type）

- fill(selector, value)：清空输入框并输入新值（推荐，大多数情况使用）
- type(selector, text)：模拟逐字输入（带延迟，更贴近真实用户）


## 实例


### 3. 键盘操作

- press：模拟按键
- keyboard.type：连续输入文本
- keyboard.press：按下某个键（可带组合键）


## 实例


### 4. 鼠标操作

Playwright 提供了完整的鼠标控制：

- hover：鼠标悬停
- mouse.move(x, y)：移动到坐标
- mouse.click(x, y)：点击坐标
- mouse.down / mouse.up：按下/释放鼠标键
- dragAndDrop：拖拽元素（Playwright 1.18+）


## 实例


## 完整实例：模拟登录并截图

下面是一个完整的 Playwright 脚本，演示了导航、定位、输入、点击等基本操作。


## 实例

运行方式：

- 在项目目录下保存代码为 github_login.js。
- 在终端中执行 node github_login.js。


## 后续章节

- 常用 API 汇总表

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Playwright 页面操作基础` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
