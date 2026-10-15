# Swagger：Swagger UI 与文档发布教程

- 来源：[Swagger UI 与文档发布](https://www.runoob.com/swagger/swagger-ui-doc.html)
- 分类：后端开发
- 技术：Swagger
- 笔记类型：练习笔记
- 章节序号：1200

## 本章内容

Swagger UI 是一种基于 OpenAPI 规范（原 Swagger 规范）的 API 文档可视化工具，它能将 API 规范文档转换为交互式 API 文档界面。

通过 Swagger UI，开发者和用户可以:

- 查看 API 的详细信息
- 直接在界面上测试 API 请求
- 查看请求和响应示例
- 了解不同 API 端点的功能和参数


### Swagger UI 的优势

- 可视化：提供清晰、直观的 API 文档界面
- 交互性：支持在线测试 API，无需额外工具
- 实时更新：代码变更后，文档自动更新
- 标准化：基于 OpenAPI 规范，保持一致性
- 跨语言支持：适用于各种编程语言和框架


## 集成 Swagger UI


### 1. 在 Spring Boot 项目中集成

在 pom.xml 添加以下依赖:


## 实例

或者使用 SpringDoc OpenAPI:


## 实例


## 实例

对于 SpringDoc OpenAPI:


## 实例


### 2. 在 Node.js Express 项目中集成

```text
npm install swagger-jsdoc swagger-ui-express --save
```


## 实例


### 3. 在 Python FastAPI 项目中使用

FastAPI 默认集成了 Swagger UI:


## 实例

Swagger UI 默认可在 /docs 路径访问，可通过访问 http://localhost:8000/docs 查看文档。

详细内容参见：FastAPI 交互式 API 文档


## 编写 API 文档


### 1. Spring Boot 项目中的 API 文档注解


## 实例

对于 SpringDoc OpenAPI:


## 实例


### 2. Node.js Express 项目中的 API 文档注释


## 实例


### 3. Python FastAPI 项目中的 API 文档


## 实例


## 自定义 Swagger UI


### 1. Spring Boot 自定义配置


## 实例


### 2. Express 自定义配置


## 实例


## 后续章节

- 3. FastAPI 自定义配置
- 实例
- 文档发布
- 1. 内部发布
- 2. 静态文档生成
- 3. 整合到 CI/CD 流程
- 实例
- 实例
- 4. 使用 API 文档管理平台
- 5. Docker 部署 Swagger UI
- 实例
- 最佳实践
- 1. 文档规范
- 2. 安全配置
- 实例
- 3. 自动化测试

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Swagger UI 与文档发布` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
