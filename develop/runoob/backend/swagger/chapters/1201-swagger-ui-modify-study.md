# Swagger：Swagger UI 主题样式修改

- 来源：[Swagger UI 主题样式修改](https://www.runoob.com/swagger/swagger-ui-modify.html)
- 分类：后端开发
- 技术：Swagger
- 笔记类型：学习笔记
- 章节序号：1201

## 本章内容

Swagger UI 提供了多种方式来自定义界面样式，让文档更符合企业或产品品牌形象。

在 Spring Boot 项目中，可以创建自定义 CSS 文件并配置 Swagger UI 使用:

创建自定义 CSS 文件，例如 src/main/resources/static/swagger-ui/custom.css:


## 实例

在 Swagger 配置中引用自定义 CSS:


## 实例

对于 SpringDoc OpenAPI:


## 实例


### 使用主题插件

对于更复杂的主题定制，可以使用 Swagger UI 主题插件。

安装主题插件(国内可以考虑其他 CDN 或者放到本地):


## 实例

对于 Express 项目:


## 实例

常见的主题包括:

- Material: theme-material.css
- Monokai: theme-monokai.css
- Muted: theme-muted.css
- Flattop: theme-flattop.css
- Feeling Blue: theme-feeling-blue.css


### 添加 Logo 和品牌标识


## 实例


## 实例


### 使用自定义模板

对于更深层次的定制，可以使用自定义 Swagger UI 模板。

1. 创建自定义模板文件 src/main/resources/templates/swagger-ui.html:


## 实例

2. 在 Spring Boot 项目中配置使用自定义模板:


## 实例


## 复习重点

- 能说明 `Swagger UI 主题样式修改` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
