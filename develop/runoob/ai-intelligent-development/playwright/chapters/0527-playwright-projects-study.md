# Playwright：Playwright 多项目配置（Projects）

- 来源：[Playwright 多项目配置](https://www.runoob.com/playwright/playwright-projects.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0527

## 本章内容

本章介绍如何通过 Projects 配置在多个浏览器和设备上运行测试，以及项目依赖的用法。


## 什么是 Project

在 Playwright 中，一个 Project 代表一组在特定浏览器和设备配置下运行的测试。

通过配置多个 Project，你可以用同一套测试代码在 Chromium、Firefox、WebKit 以及移动端设备上运行。


## 基础多浏览器配置


## 实例

运行特定浏览器的测试：

```text
# 仅在 Chromium 上运行
npx playwright test --project=chromium

# 在 Chromium 和 Firefox 上运行
npx playwright test --project=chromium --project=firefox
```


## devices 设备预设

Playwright 内置了大量设备预设（来自 @playwright/test 的 devices），模拟真实设备的视口、User-Agent、像素比等。


## 实例

常用的设备预设：


## 自定义项目配置

你可以在 Project 的 use 中覆盖全局配置：


## 实例


## 项目依赖（dependencies）

一个项目可以依赖另一个项目，确保依赖的项目先运行。

最常见的用法是 Setup 项目（认证）先运行，其他项目依赖它。


## 实例

setup 项目只会运行一次，所有依赖它的项目会等待它完成后才启动。


## 通过 testProject 共享配置

如果要让多个项目共享配置而不重复，可以提取一个基础项目：


## 实例


## 复习重点

- 能说明 `Playwright 多项目配置` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
