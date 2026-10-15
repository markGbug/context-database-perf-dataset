# Playwright：Playwright 网络监控与 API 测试

- 来源：[Playwright 网络监控](https://www.runoob.com/playwright/playwright-network-monitor.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：学习笔记
- 章节序号：0532

## 本章内容

本章介绍如何监控浏览器网络流量，以及使用 Playwright 进行独立的 API 测试。


## 监听网络请求与响应


### page.on('request') 监听请求


## 实例


### page.on('response') 监听响应


## 实例


## page.waitForResponse() 等待特定响应


## 实例


## Console 消息监听


## 实例


### ConsoleMessage 类型


## API 测试（request fixture）

Playwright 的 request fixture 允许你不通过浏览器直接发送 HTTP 请求。

这非常适合在测试前后准备或清理服务端状态。


### 发送 GET 请求


## 实例


### 发送 POST 请求


## 实例


### 配置 baseURL 和认证头


## 实例


## API + 浏览器组合测试

在实际项目中，常常在操作浏览器前后使用 API 进行状态管理。


## 实例

API 测试比浏览器操作快得多，适合用于数据准备和清理。将 API 和浏览器操作结合使用，可以大大提高测试的效率和可靠性。


## 复习重点

- 能说明 `Playwright 网络监控` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
