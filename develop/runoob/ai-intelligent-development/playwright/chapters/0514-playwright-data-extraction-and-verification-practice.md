# Playwright：Playwright 数据提取和验证

- 来源：[Playwright 数据提取和验证](https://www.runoob.com/playwright/playwright-data-extraction-and-verification.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：练习笔记
- 章节序号：0514

## 本章内容

数据提取和验证是自动化测试的关键，主要包括 获取页面数据、断言验证、截图和录制，不仅能验证功能是否正确，还能辅助调试和回归测试。


## 元素信息获取

在测试中经常需要读取页面信息进行验证，Playwright 提供了丰富的 API。


### 1. 获取文本内容


## 实例


### 2. 获取属性值

```javascript
const value = await page.getAttribute('#username', 'placeholder');
console.log(value); // "请输入用户名"
```


### 3. 获取样式信息

```javascript
// 获取元素的 style 属性
const color = await page.$eval('#btn', el => getComputedStyle(el).color);
console.log(color);
```


### 4. 元素状态检查

```text
await page.isVisible('#dialog');   // 是否可见
await page.isHidden('#loading');   // 是否隐藏
await page.isEnabled('#submit');   // 是否可用
await page.isDisabled('#submit');  // 是否禁用
await page.isChecked('#agree');    // 复选框是否选中
```


## 断言和验证

Playwright 提供了 内置断言库（@playwright/test），便于编写测试用例。


### 1. 内置断言方法

在 @playwright/test 中，使用 expect 进行断言。


## 实例


### 2. 文本内容验证

```text
await expect(page.locator('#message')).toHaveText('登录成功');
await expect(page.locator('#username')).toHaveValue('testuser');
```


### 3. 元素状态验证

```text
await expect(page.locator('#submit')).toBeEnabled();
await expect(page.locator('#agree')).toBeChecked();
await expect(page.locator('#loading')).toBeHidden();
```


### 4. 页面标题和 URL 验证

```text
await expect(page).toHaveTitle(/Playwright/);
await expect(page).toHaveURL('https://playwright.dev/');
```


## 截图和录制

截图与录制在调试、失败用例分析和回归测试中非常有用。


### 1. 页面截图

```text
await page.screenshot({ path: 'screenshot.png', fullPage: true });
```

- path: 保存路径
- fullPage: 是否截取整个页面


### 2. 元素截图

```javascript
const element = page.locator('#logo');
await element.screenshot({ path: 'logo.png' });
```


### 3. 视频录制

在创建 context 时启用录制：

```javascript
const context = await browser.newContext({
  recordVideo: { dir: 'videos/' }
});
const page = await context.newPage();
await page.goto('https://example.com');
await context.close(); // 关闭后保存视频
```


### 4. 截图对比（快照测试）

Playwright 支持快照对比，常用于回归测试。

```text
import { test, expect } from '@playwright/test';

test('页面快照测试', async ({ page }) => {
  await page.goto('https://playwright.dev');
  expect(await page.screenshot()).toMatchSnapshot('homepage.png');
});
```

会将截图与基准图像 homepage.png 对比，检测 UI 变化。

好的 ✅ 那我来为 第六章：数据提取和验证 补充一个 完整实战案例，并整理出 API 对照表。这样你就能既有实战，又能快速查表。


## 实战案例 —— 登录验证与截图快照

这个案例涵盖了：信息提取 + 断言验证 + 页面截图。


## 实例

这个测试会验证：

- 页面标题和欢迎文本是否正确
- 元素是否可见 / 可用
- 用户信息属性是否存在
- 页面截图和 UI 快照对比


## 常用 API 表格

下面是 数据提取与验证相关 API 一览表。


### 断言与验证（@playwright/test）


### 截图与录制


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Playwright 数据提取和验证` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
