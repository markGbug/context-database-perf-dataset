# Swagger：Swagger 简介

- 来源：[Swagger 简介](https://www.runoob.com/swagger/swagger-intro.html)
- 分类：后端开发
- 技术：Swagger
- 笔记类型：练习笔记
- 章节序号：1195

## 本章内容

Swagger 是一套用于 API 开发、文档生成和交互测试的开源工具集。

Swagger最早由 Wordnik 的联合创始人 Tony Tam 在 2011 年创建。它通过简洁的 JSON 或 YAML 格式描述 API 结构，使得 API 的设计、实现和测试更加高效直观。Swagger 后来演变为 OpenAPI Specification，并成为业界广泛接受的标准。

Swagger 的主要组成部分包括：

- Swagger UI：Swagger UI 是一个可视化工具，可以将 OpenAPI 规范呈现为交互式 API 文档。它允许用户直接在浏览器中查看和测试 API。
- Swagger Editor：Swagger Editor 是一个基于浏览器的编辑器，用于编写 OpenAPI 规范。它提供实时预览和验证功能。
- Swagger Codegen：Swagger Codegen 可以根据 OpenAPI 规范生成服务器存根和客户端 SDK，支持 40 多种语言。
- Swagger Hub：Swagger Hub 是一个集成的 API 设计和文档平台，提供协作功能和云存储。


## Swagger 的发展历程

- 2011 年：Tony Tam 在开发 Wordnik 产品时，设计了 Swagger 的雏形。
- 2011 年 9 月：Swagger 项目正式开源，支持 Node.js 和 Ruby on Rails。
- 2013 年：尽管 API Blueprint 和 RAML 出现，但 Swagger 增长更快。
- 2015 年：发起 OpenAPI Initiative，获得 Google、IBM、Microsoft 等支持。
- 2016 年：Swagger 规范更名为 OpenAPI Specification。
- 2017 年：Swagger 工具的日下载量超过 10 万次，成为 API 开发的重要工具。


## Swagger 的核心概念


### OpenAPI 规范

Swagger 的核心是 OpenAPI 规范（以前称为 Swagger 规范），这是一种与语言无关的标准，用于描述 RESTful API。它使用 YAML 或 JSON 格式定义 API 的：

- 端点（Endpoints）
- 操作（Operations）
- 参数（Parameters）
- 请求/响应格式
- 认证方法


### API 文档

Swagger 自动从代码生成交互式 API 文档，这些文档允许开发者：

- 查看所有可用的 API 端点
- 测试 API 调用
- 查看请求和响应示例
- 了解所需的参数和头信息


## 为什么选择 Swagger？

- 标准化：Swagger 是 OpenAPI 的前身，也是目前最主流的 API 描述标准。
- 自动化：支持自动生成 API 文档、SDK 和服务端代码，减少重复劳动。
- 交互性强：Swagger UI 提供所见即所得的交互界面，降低调试难度。
- 社区与支持广泛：大厂如 Google、IBM、Microsoft 等都对 Swagger 提供支持，社区活跃，插件丰富。


## Swagger 的优势


### 1. 提高开发效率

Swagger 通过自动生成 API 文档和客户端代码，显著减少了手动编写文档的时间，让开发者可以更专注于业务逻辑的实现。


### 2. 改善团队协作

清晰的 API 文档使前端和后端开发人员能够更好地协作，减少沟通成本。


### 3. 简化 API 测试

内置的交互式界面允许开发者和测试人员直接在浏览器中测试 API，无需额外的测试工具。


### 4. 支持多种语言

Swagger 支持几乎所有主流编程语言，包括 Java、Python、Node.js、.NET 等。


## 如何使用 Swagger


### 基本使用步骤

- 定义 API 规范：使用 Swagger Editor 编写 OpenAPI 规范文件
- 生成文档：使用 Swagger UI 展示 API 文档
- 生成代码：使用 Swagger Codegen 生成服务器存根或客户端 SDK
- 测试 API：通过 Swagger UI 进行 API 测试


### 示例代码

以下是一个简单的 OpenAPI 规范示例（YAML 格式）：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Swagger 简介` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
