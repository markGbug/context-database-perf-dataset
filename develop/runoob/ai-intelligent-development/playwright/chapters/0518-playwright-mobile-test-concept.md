# Playwright：Playwright 移动端测试

- 来源：[Playwright 移动端测试](https://www.runoob.com/playwright/playwright-mobile-test.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0518

## 本章内容

Playwright 移动端测试，主要包括模拟移动设备、地理位置、权限控制等功能。

Playwright 除了能模拟桌面浏览器，还支持 移动端设备测试，包括：

- 模拟不同手机型号（屏幕大小、分辨率、UA 等）
- 模拟触摸事件（点击、滑动、长按）
- 模拟地理位置（GPS）
- 模拟权限（摄像头、定位、通知）

这让我们能在 PC 上测试出接近真实手机的效果。


## 模拟设备

Playwright 提供了一些常见的设备配置（基于 Chrome DevTools 设备描述），可以通过 devices 调用。


## 实例


### 可模拟内容：

- 屏幕分辨率（width、height、deviceScaleFactor）
- User-Agent（模拟移动 UA）
- 触摸事件支持
- 横竖屏切换


## 模拟触摸操作

Playwright 在移动设备模式下会启用 触摸事件。


### 常用操作：

1、轻点

```text
await page.tap('button#submit');
```

2、滑动/拖动

```text
await page.touchscreen.tap(200, 300); // 点击指定坐标
await page.touchscreen.swipe(200, 300, 200, 800); // 自定义封装，模拟滑动
```

3、长按

```text
await page.touchscreen.down(200, 300);
await page.waitForTimeout(1000); // 按住 1 秒
await page.touchscreen.up();
```


## 模拟地理位置

可以模拟手机的 GPS 定位。


## 实例


## 模拟权限

Playwright 支持授予或拒绝常见权限，例如：

- geolocation（地理位置）
- camera（摄像头）
- microphone（麦克风）
- notifications（通知）

```javascript
const context = await browser.newContext({
  permissions: ['geolocation', 'notifications']
});
```


## 模拟横竖屏切换

通过修改 viewport 配置实现。

```text
await context.newPage({
  viewport: { width: 812, height: 375 }, // 横屏
  isMobile: true
});
```


## 完整实例：移动端测试


## 实例


## 常用 API


## 常见设备

Playwright 内置常见设备清单，包含 iPhone 系列、Pixel 系列、iPad 等。


### Playwright 常见设备清单

Playwright 内置了几十种常用设备配置（基于 Chrome DevTools 数据）。使用时通过：

```javascript
const { devices } = require('playwright');
const iphone = devices['iPhone 12'];
```

即可获得该设备的配置参数。


### iPhone 系列


### Google Pixel 系列


### iPad 系列


### 其他 Android 机型


### 使用方法


## 实例


## 记忆卡片

- 一句话定义：`Playwright 移动端测试` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
