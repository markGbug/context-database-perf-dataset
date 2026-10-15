# Playwright：Playwright 配置详解

- 来源：[Playwright 配置详解](https://www.runoob.com/playwright/playwright-config.html)
- 分类：AI / 智能开发
- 技术：Playwright
- 笔记类型：概念卡
- 章节序号：0526

## 本章内容

本章详细介绍 playwright.config.ts 中的各项配置，让你能够根据项目需求灵活调整测试行为。


## 配置文件概览

playwright.config.ts 是 Playwright 的中央配置文件，所有测试运行参数都在此定义。


## 实例


## 基础配置项


### 配置示例


## 实例


## use 公共配置

use 中的配置会应用到所有测试和项目：


## webServer 配置

webServer 配置让 Playwright 在运行测试前自动启动你的开发服务器：


## 实例


## globalSetup / globalTeardown 全局钩子

在所有测试运行之前/之后执行一次，适合数据库初始化等操作。


## 实例


## 实例


## 记忆卡片

- 一句话定义：`Playwright 配置详解` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
