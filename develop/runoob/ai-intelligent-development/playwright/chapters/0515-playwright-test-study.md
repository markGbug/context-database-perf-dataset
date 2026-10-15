# Playwright：Playwright Test

- 来源：[Playwright Test](https://www.runoob.com/playwright/playwright-test.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0515

## 本章内容

Playwright 除了作为浏览器自动化工具，还自带了一个 完整的测试框架 —— Playwright Test。

Playwright Test 可以帮助我们组织测试用例、生成报告、并行执行、失败重试，功能完备，开箱即用。

- Playwright Test 是一个 集成的测试框架，无需额外依赖。
- 配置文件可设置 超时、重试、报告、浏览器项目等。
- 测试用例支持 分组、钩子、数据驱动。
- 提供 并行执行、HTML 报告、失败重试 等高级能力。


## 测试框架概述

- 集成测试框架：自带测试运行器，无需额外安装 Jest、Mocha。
- 内置断言库：支持 expect 断言。
- 测试隔离：每个 test 默认在新的浏览器上下文中执行，互不干扰。
- 丰富功能：并行执行、重试、截图、录制、HTML 报告等。

安装方式：

```text
npm init playwright@latest
```

自动生成项目结构，包含配置文件 playwright.config.js。


### 1. 配置文件详解

Playwright Test 使用 playwright.config.js（或 .ts）作为配置入口。

```text
// playwright.config.js
import { defineConfig } from '@playwright/test';

export default defineConfig({
  testDir: './tests',         // 测试目录
  timeout: 30 * 1000,         // 单个测试超时时间
  retries: 2,                 // 失败重试次数
  reporter: [['html'], ['list']], // 测试报告类型
  use: {
    headless: true,           // 是否无头模式
    screenshot: 'only-on-failure', // 失败时截图
    video: 'retain-on-failure',    // 失败时保留视频
    baseURL: 'https://example.com', // 基础 URL
  },
  projects: [
    { name: 'Chromium', use: { browserName: 'chromium' } },
    { name: 'Firefox',  use: { browserName: 'firefox' } },
    { name: 'WebKit',   use: { browserName: 'webkit' } },
  ],
});
```


### 2. 测试脚本结构

Playwright Test 脚本通常包含：

1、导入测试库

```text
  import { test, expect } from '@playwright/test';
```

2、编写测试用例

```text
test('示例测试', async ({ page }) => {
  await page.goto('https://example.com');
  await expect(page).toHaveTitle('Example Domain');
});
```

3、分组与钩子

- 使用 describe 组织测试
- 使用 beforeEach / afterEach 做前后置处理


## 编写测试用例


### 1. test() 函数使用

```text
test('页面标题验证', async ({ page }) => {
  await page.goto('https://playwright.dev');
  await expect(page).toHaveTitle(/Playwright/);
});
```


### 2. describe() 分组

```text
test.describe('用户登录模块', () => {
  test('输入正确账号密码', async ({ page }) => {
    // 登录逻辑...
  });

  test('输入错误密码', async ({ page }) => {
    // 验证错误提示...
  });
});
```


### 3. 测试钩子

```text
test.describe('购物车模块', () => {
  test.beforeEach(async ({ page }) => {
    await page.goto('https://example.com/cart');
  });

  test.afterEach(async ({ page }) => {
    await page.screenshot({ path: 'cart.png' });
  });

  test('添加商品', async ({ page }) => {
    await page.click('#add-item');
    await expect(page.locator('#cart-count')).toHaveText('1');
  });
});
```


### 4. 测试数据准备

支持参数化测试：

```java
const users = [
  { name: 'admin', password: '123456' },
  { name: 'guest', password: 'guest' },
];

for (const user of users) {
  test(`用户 ${user.name} 登录`, async ({ page }) => {
    await page.goto('https://example.com/login');
    await page.fill('#username', user.name);
    await page.fill('#password', user.password);
    await page.click('#submit');
    await expect(page.locator('.welcome')).toBeVisible();
  });
}
```


## 运行和报告


### 1. 测试执行命令

```text
npx playwright test          # 运行全部测试
npx playwright test login.spec.js   # 运行单个文件
npx playwright test -g "登录"       # 运行指定用例
```


### 2. 并行测试

Playwright 默认 按文件并行执行，也可在配置文件中指定 workers 数量：

```text
npx playwright test --workers=4
```


### 3. 测试报告生成

运行后生成 HTML 报告：

```text
npx playwright show-report
```


### 4. 失败重试机制

在配置文件 playwright.config.js 中设置：

```text
retries: 2
```

测试失败时会自动重试，适合处理偶发性错误。

- Playwright Test 是一个 集成的测试框架，无需额外依赖。
- 配置文件可设置 超时、重试、报告、浏览器项目等。
- 测试用例支持 分组、钩子、数据驱动。
- 提供 并行执行、HTML 报告、失败重试 等高级能力。


## 完整测试套件示例


### 1、项目结构

```text
playwright-demo/
├─ playwright.config.ts           # 全局配置（多项目、多浏览器、报告、重试…）
├─ package.json
├─ tests/
│  ├─ auth.setup.ts               # 一次性登录，生成 storageState
│  ├─ smoke/
│  │  └─ home.spec.ts             # 冒烟用例：标题/URL/截图对比
│  └─ e2e/
│     └─ cart.spec.ts             # 端到端：添加购物车、断言、附件、步骤
├─ fixtures/
│  ├─ pages.ts                    # 页面对象（PO）
│  └─ test.extend.ts              # 自定义 fixtures
└─ snapshots/                     # 视觉基线（自动生成）
```


### 2、配置文件（playwright.config.ts）


## 实例

要点：projects 让同一套用例在不同浏览器/配置下运行；use 可在全局/项目/测试三级覆盖；报告与重试在配置中统一管理。


### 3、夹具与页面对象

fixtures/test.extend.ts（自定义 fixture + 公共步骤封装）


## 实例

基于 test.extend() 增加自定义 fixture，便于在任意用例中直接注入 home、cart 实例。

fixtures/pages.ts（页面对象）


## 实例


### 4、前置登录（一次性生成 storageState）

tests/auth.setup.ts（仅在 "setup" 项目里执行）


## 实例


### 5、冒烟测试（标题/URL/视觉对比）

tests/smoke/home.spec.ts


## 实例

视觉对比建议使用 toHaveScreenshot（优先于用 page.screenshot() + toMatchSnapshot 的手写方式）。


## 后续章节

- 6、端到端测试（步骤、附件、断言）
- 实例
- 7、运行与报告
- 常用相关 API 速查表（Playwright Test）
- 1、测试与分组
- 2、夹具与配置
- 3、断言（expect）
- 4、步骤与附件
- 5、报告与 CLI

## 复习重点

- 能说明 `Playwright Test` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
