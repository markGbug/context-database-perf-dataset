# Swagger：OpenAPI 规范基础

- 来源：[OpenAPI 规范基础](https://www.runoob.com/swagger/openapi-basic.html)
- 分类：后端开发
- 技术：Swagger
- 笔记类型：练习笔记
- 章节序号：1197

## 本章内容

OpenAPI 规范（OAS）是一种用于描述 RESTful API 的标准格式。

OpenAPI 规范允许开发者以机器可读的方式定义 API 的结构、参数、响应等信息。

OpenAPI 规范最初被称为 Swagger 规范，后来被捐赠给 OpenAPI Initiative 并更名为 OpenAPI。

OpenAPI 规范的主要作用包括：

- 提供 API 的标准化文档
- 支持 API 的自动化测试
- 生成客户端 SDK
- 促进前后端分离开发

OpenAPI 目前主要有两个广泛使用的版本：

- OpenAPI 2.0（原 Swagger 2.0）
- OpenAPI 3.x（最新稳定版本）

建议新项目使用 OpenAPI 3.x 版本，因为它提供了更多功能和改进。


### OpenAPI 规范的结构

OpenAPI 文档通常以 YAML 或 JSON 格式编写。

下面是一个基本的 OpenAPI 文档结构：


## 实例


## OpenAPI 核心概念详解


### 1. 文档元数据 (info)

info 部分包含 API 的基本信息，如标题、描述、版本等：


## 实例


### 2. 服务器信息 (servers)

servers 部分定义可用的 API 服务器列表：


## 实例


### 3. 路径 (paths)

paths 部分定义 API 的所有端点和它们支持的 HTTP 方法：


## 实例


### 4. 操作 (operations)

每个路径下的 HTTP 方法定义了一个 API 操作：


## 实例


### 5. 参数 (parameters)

参数可以定义在多个位置：


## 实例


### 6. 请求体 (requestBody)

定义 POST、PUT 等方法的请求体：


## 实例


### 7. 响应 (responses)

定义每个操作可能的响应：


## 实例


### 8. 组件 (components)

components 部分用于存储可在整个 API 文档中重用的元素：


## 实例


### 9. 数据模型 (schemas)

定义 API 中使用的数据结构：


## 实例


### 10. 安全 (security)

定义 API 的认证和授权方法：


## 实例


## 创建完整的 OpenAPI 文档实例

下面是一个更完整的电子商务 API 示例：


## 后续章节

- 实例
- OpenAPI 规范的基本语法
- YAML 格式示例
- 实例
- JSON 格式示例
- 实例
- 如何使用 OpenAPI 规范
- 1. 创建和编辑 OpenAPI 文档
- 2. 文档生成
- 3. 代码生成
- 4. API 测试和模拟
- 最佳实践
- 1. 设计原则
- 2. 文档建议
- 3. 版本控制策略
- 常见问题解答

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `OpenAPI 规范基础` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
