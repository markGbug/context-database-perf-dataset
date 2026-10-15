# Playwright：Playwright 高级页面操作

- 来源：[Playwright 高级页面操作](https://www.runoob.com/playwright/playwright-advanced-page-operations.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0513

## 本章内容

本章节我们将介绍 Playwright 高级页面操作，这部分会更贴近真实测试需求，覆盖 等待机制、表单处理、弹窗对话框 等高级功能。


## 等待机制

Playwright 最大的优势之一就是 智能等待（auto-waiting）：大部分操作（如 click, fill）会自动等待元素可见且可操作。但在复杂场景中，仍需要手动控制等待。


### 1. 隐式等待（Auto-waiting）

Playwright 内置的等待机制：

- 元素可见
- 可点击 / 可交互
- 页面加载完成


## 实例


### 2. 显式等待

显式调用等待方法，例如等待某个选择器、文本或请求。


## 实例

常见 state 值：

- 'attached' → 元素出现在 DOM 中
- 'visible' → 元素在页面可见
- 'hidden' → 元素隐藏
- 'detached' → 元素被移除


### 3. 等待元素出现 / 消失

```text
// 等待元素出现
await page.waitForSelector('#loading', { state: 'visible' });

// 等待元素消失
await page.waitForSelector('#loading', { state: 'hidden' });
```


### 4. 等待网络请求完成

等待某个请求完成，常用于 AJAX 请求或 API 调用。

```text
// 等待指定 URL 的请求完成
await page.waitForResponse(response =>
  response.url().includes('/api/login') && response.status() === 200
);
```


### 5. 自定义等待条件

通过 page.waitForFunction 执行自定义等待逻辑。

```text
// 等待页面上计数器达到 10
await page.waitForFunction(() => {
  return document.querySelector('#count').innerText === '10';
});
```


## 表单处理

表单是测试中最常见的交互场景。Playwright 提供了丰富的 API 来操作表单控件。


### 1. 输入框操作

```text
await page.fill('#username', 'admin');  // 清空并输入
await page.type('#search', 'Playwright', { delay: 100 }); // 模拟逐字输入
```


### 2. 下拉菜单选择

```text
// 通过 value
await page.selectOption('#country', 'china');

// 通过标签文本
await page.selectOption('#country', { label: 'United States' });

// 通过 index
await page.selectOption('#country', { index: 2 });
```


### 3. 复选框和单选框

```text
// 勾选复选框
await page.check('#agree');

// 取消勾选
await page.uncheck('#subscribe');

// 点击单选框
await page.check('input[type="radio"][value="male"]');
```


### 4. 文件上传

```text
// 直接上传文件
await page.setInputFiles('#upload', 'example.png');

// 上传多个文件
await page.setInputFiles('#upload', ['a.png', 'b.png']);

// 清空文件
await page.setInputFiles('#upload', []);
```


### 5. 表单提交

提交表单有两种方式：

- 点击提交按钮
- 直接触发表单提交事件

```text
await page.click('button[type="submit"]');
// 或者
await page.press('#form input[name="email"]', 'Enter');
```


## 弹窗和对话框

Playwright 可以捕获并处理 浏览器原生弹窗（alert, confirm, prompt），以及自定义模态框。


### 1. Alert 处理

```javascript
page.once('dialog', async dialog => {
  console.log(dialog.message()); // 打印弹窗内容
  await dialog.accept(); // 点击 "确定"
});

await page.click('#show-alert');
```


### 2. Confirm 处理

```javascript
page.once('dialog', async dialog => {
  console.log(dialog.message());
  await dialog.dismiss(); // 点击 "取消"
});

await page.click('#show-confirm');
```


### 3. Prompt 处理

```javascript
page.once('dialog', async dialog => {
  console.log(dialog.message());
  await dialog.accept('Playwright'); // 输入内容并确认
});

await page.click('#show-prompt');
```


### 4. 自定义模态框

自定义模态框（如 Bootstrap / Ant Design）其实就是普通 DOM 元素，可以直接用 定位 + 交互 的方式关闭或输入。

```text
await page.click('#open-modal');
await page.fill('.modal input[name="name"]', 'Test User');
await page.click('.modal button.confirm');
```


## 实战案例 —— 注册表单自动化测试

下面的示例会综合使用 等待机制、表单操作、文件上传、对话框处理。


## 实例

运行后效果：

- 自动填写表单、选择国家、上传头像
- 自动处理弹窗
- 提交后截图并验证欢迎信息


## 完整 API

以下整理了 页面导航、等待、表单、交互、弹窗 的常用 API：


## 记忆卡片

- 一句话定义：`Playwright 高级页面操作` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
