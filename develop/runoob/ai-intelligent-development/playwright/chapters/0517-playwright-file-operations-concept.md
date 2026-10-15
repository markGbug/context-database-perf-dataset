# Playwright：Playwright 文件操作

- 来源：[Playwright 文件操作](https://www.runoob.com/playwright/playwright-file-operations.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0517

## 本章内容

虽然 Playwright 主要是做浏览器自动化的，但它在文件上传和下载方面也很强大，可以轻松应对前端常见的文件交互场景。


## 文件上传

在 Web 表单中，文件上传通常通过 <input type="file"> 完成。Playwright 提供了专门的 API 来处理：


### 方法一：setInputFiles()

```text
await page.setInputFiles('input[type="file"]', 'tests/fixtures/avatar.png');
```

- 参数说明： 选择器：文件选择框的定位方式。 文件路径：相对/绝对路径，支持单文件或多文件数组。
- 如果传入 []，表示清空已选择的文件。


### 方法二：直接通过 Locator

```javascript
const upload = page.locator('input[type=file]');
await upload.setInputFiles(['tests/fixtures/1.png', 'tests/fixtures/2.png']);
```


### 方法三：模拟拖拽上传（部分应用支持）

```javascript
const fileChooserPromise = page.waitForEvent('filechooser');
await page.click('button#upload'); // 触发选择文件
const fileChooser = await fileChooserPromise;
await fileChooser.setFiles('tests/fixtures/test.pdf');
```


## 文件下载

Playwright 可以捕获浏览器下载事件，并获取文件保存路径。


### 基本用法：监听下载


## 实例


## 截图与录屏文件

Playwright 本身也会生成文件（截图、视频、trace 等）：

```text
await page.screenshot({ path: 'screenshots/home.png', fullPage: true });
await page.video()?.saveAs('videos/test.mp4');  // 在配置中开启 video 记录才可用
```


## 文件操作完整示例


## 实例


## 文件操作 API


## 记忆卡片

- 一句话定义：`Playwright 文件操作` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
