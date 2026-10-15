# Playwright：Playwright 网络拦截与 Mock

- 来源：[Playwright 网络拦截](https://www.runoob.com/playwright/playwright-network-mock.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0531

## 本章内容

本章介绍如何使用 Playwright 拦截、修改和模拟网络请求，实现不依赖后端 API 的独立测试。


## 什么是网络拦截

网络拦截允许你在浏览器发起 HTTP 请求时进行干预。

你可以阻止请求、修改响应、返回模拟数据，让测试不依赖外部 API 或网络状态。


## page.route() 拦截请求

page.route(url, handler) 用于拦截匹配指定 URL 模式的所有网络请求。


### 基本拦截


## 实例

URL 匹配模式支持以下格式：


## route.abort() 阻止请求


## 实例


## route.fulfill() 模拟响应

route.fulfill() 是最强大的 Mock 方法，可以返回任意自定义响应。


### Mock JSON 数据


## 实例


### Mock 错误响应


## 实例


## route.continue() 修改后继续

不是直接返回模拟数据，而是修改真实请求或响应后继续发送到服务器。


## 实例


## route.fetch() 真实请求

在 Mock 处理函数中，可以用 route.fetch() 实际发送请求并获取真实响应，然后修改。


## 实例


## Context 级拦截 vs Page 级拦截


## 实例


## HAR 文件录制与回放

HAR（HTTP Archive）文件可以记录页面的所有网络请求，然后回放模拟。


## 实例

```text
# 录制 HAR 文件
npx playwright open --save-har=tests/hars/api-responses.har https://www.runoob.com/
```

HAR 文件适合 Mock 大量或复杂的 API 响应。先录制一次，之后测试都从 HAR 回放，不依赖真实服务器。


## 记忆卡片

- 一句话定义：`Playwright 网络拦截` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
