# Playwright：Playwright 扩展与迁移

- 来源：[Playwright 扩展与迁移](https://www.runoob.com/playwright/playwright-extensions.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0543

## 本章内容

本章介绍 Playwright 生态的扩展功能，包括 Library 脚本模式、MCP 服务、Test Agents，以及从其他框架迁移到 Playwright 的指南。


## Playwright Library 脚本模式

Playwright Library 是单独的浏览器自动化库，适用于测试运行器之外的场景。


### 安装

```text
npm i playwright
```


### 典型用法


## 实例


### PDF 生成


## 实例


### Library 模式 vs Test Runner 的选择


## Playwright MCP 简介

Playwright MCP（Model Context Protocol）服务器让 AI 助手可以直接控制浏览器。


### MCP 安装与配置

```text
# 为 Claude Code 添加 Playwright MCP
claude mcp add playwright npx @playwright/mcp@latest
```

在 VS Code 或其他 MCP 客户端中配置：


## 实例


### MCP 的工作方式

AI Agent 通过结构化的可访问性快照（Accessibility Snapshot）来感知页面内容。

每条可访问性信息有一个 ref 标识，Agent 通过这个 ref 来进行点击、输入等操作。

这种方式不需要截图，完全基于结构化数据交互，速度快且确定性高。


## Playwright Test Agents

Test Agents 是实验性的 AI 驱动测试工具，可以自动生成和修复测试。

初始化 Test Agents：

```text
# 为 VS Code 初始化
npx playwright init-agents --loop=vscode

# 为 Claude Code 初始化
npx playwright init-agents --loop=claude
```


## 组件测试概览（实验性）

Playwright 支持直接挂载和测试 React/Vue 组件，无需完整的页面环境。


## 实例


## 无障碍测试

Playwright 提供了无障碍名称和描述的断言，帮助验证页面的可访问性。


## 实例


## 从其他框架迁移


### 从 Puppeteer 迁移

Playwright 与 Puppeteer 共享 Chrome DevTools Protocol 的能力，迁移相对简单。


### 从 Cypress 迁移

Playwright 的 Locator 理念与 Cypress 的查询链类似，但有一些关键差异：


### 从 Selenium 迁移

Selenium 使用 WebDriver 协议，Playwright 直接控制浏览器协议，API 风格差异较大。

迁移建议：不要试图一步完成所有测试的迁移。

先选择一两个核心功能的测试用 Playwright 重写，验证通过后再逐步迁移其余测试。


## 记忆卡片

- 一句话定义：`Playwright 扩展与迁移` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
