# Playwright：Playwright 设备与浏览器模拟

- 来源：[Playwright 设备与浏览器模拟](https://www.runoob.com/playwright/playwright-emulation.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0535

## 本章内容

本章介绍如何在 Playwright 中模拟移动设备、地理位置、时区、语言、颜色方案等浏览器环境参数。


## 移动端设备模拟

Playwright 内置了大量设备预设，可以模拟各种手机和平板的视口、User-Agent 和触控行为。


### 使用 devices 预设

通过 devices 对象可以快速模拟特定设备。


## 实例

在配置文件中使用设备预设：


## 实例


### 手动配置视口

如果你不需要完整的设备预设，也可以手动指定视口大小。


## 实例


## 地理位置模拟

Playwright 可以模拟设备的 GPS 位置信息。


## 实例


## 时区与语言模拟

通过设置 locale 和 timezone 来验证国际化和时区相关的功能。


## 实例

常用的 locale 值：


## 颜色方案模拟

模拟浅色或深色模式，测试 prefers-color-scheme 媒体查询的效果。


## 实例

在配置文件中为不同项目设置不同的颜色方案：


## 实例


## 权限模拟

使用 context.grantPermissions() 来授予浏览器权限。


## 实例


## Cookie 操作

通过 BrowserContext 可以读取、添加和清除 Cookie。


## 实例


### Cookie 参数说明


## localStorage 与 SessionStorage 操作

通过 page.evaluate() 在页面上下文操作存储。


## 实例

Cookie 和 Storage 操作都应该在 page.goto() 之前完成，确保页面加载时就能使用这些数据。


## 复习重点

- 能说明 `Playwright 设备与浏览器模拟` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
