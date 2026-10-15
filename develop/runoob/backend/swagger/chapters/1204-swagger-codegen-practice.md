# Swagger：Swagger Codegen（代码生成）

- 来源：[Swagger Codegen](https://www.runoob.com/swagger/swagger-codegen.html)
- 分类：后端开发
- 技术：Swagger
- 笔记类型：练习笔记
- 章节序号：1204

## 本章内容

Swagger 是一套围绕 OpenAPI 规范(以前称为 Swagger 规范)构建的开源工具，用于设计、构建、记录和使用 RESTful Web 服务。

Swagger 主要包括:

- Swagger Editor: 基于浏览器的编辑器，可以编写 OpenAPI 规范
- Swagger UI: 可视化 API 文档界面，允许开发者交互式地探索 API
- Swagger Codegen: 根据 OpenAPI 规范自动生成客户端代码和服务器存根

OpenAPI 规范是一个与语言无关的定义格式，用于描述 RESTful APIs。

OpenAPI 允许人类和计算机发现和理解服务的功能，而无需访问源代码或额外文档。


## Swagger Codegen（代码生成）


### 环境准备

在开始之前，确保你的系统中已安装:

- Java 8+
- Maven (用于Java项目)
- Git (用于获取源代码)

安装 Swagger Codegen:

```text
# 方法1: 使用homebrew (macOS)
brew install swagger-codegen

# 方法2: 从GitHub下载JAR文件
wget https://repo1.maven.org/maven2/io/swagger/codegen/v3/swagger-codegen-cli/3.0.36/swagger-codegen-cli-3.0.36.jar -O swagger-codegen-cli.jar
java -jar swagger-codegen-cli.jar help
```


### 生成客户端 SDK

以 Petstore API 为例生成 Java 客户端:

```text
# 使用命令行工具
swagger-codegen generate -i https://petstore.swagger.io/v2/swagger.json -l java -o ./java-client

# 或使用JAR文件
java -jar swagger-codegen-cli.jar generate \
  -i https://petstore.swagger.io/v2/swagger.json \
  -l java \
  -o ./java-client
```

生成的客户端 SDK 结构:

```text
java-client/
├── pom.xml                  # Maven项目文件
├── README.md                # 说明文档
├── src/
│   ├── main/
│   │   ├── java/           # 生成的Java代码
│   │   └── resources/      # 配置文件
│   └── test/               # 测试代码
└── .gitignore
```

使用生成的 Java 客户端:


## 实例

生成 Python 客户端:

```text
swagger-codegen generate -i https://petstore.swagger.io/v2/swagger.json -l python -o ./python-client
```

Python 客户端使用示例:


## 实例

Swagger Codegen 支持多种语言和框架，包括但不限于:

- JavaScript/TypeScript (Node.js, Angular, React等)
- Ruby
- PHP
- C#/.NET
- Go
- Swift
- Kotlin
- Scala

查看支持的语言列表:

```text
swagger-codegen langs
```


### 生成服务端桩代码

生成 Spring Boot 服务器存根:

```text
swagger-codegen generate \
  -i https://petstore.swagger.io/v2/swagger.json \
  -l spring \
  -o ./spring-server
```

生成的Spring服务端代码结构:

```text
spring-server/
├── pom.xml                  # Maven项目文件
├── README.md                # 说明文档
├── src/
│   ├── main/
│   │   ├── java/           # 控制器接口和模型类
│   │   └── resources/      # 配置文件和静态资源
│   └── test/               # 测试代码
└── .gitignore
```

实现生成的控制器接口:


## 实例

生成 Node.js 服务器代码:

```text
swagger-codegen generate \
  -i https://petstore.swagger.io/v2/swagger.json \
  -l nodejs-server \
  -o ./nodejs-server
```

Node.js 服务端使用示例:


## 实例


## OpenAPI Generator 进阶


### OpenAPI Generator vs Swagger Codegen

OpenAPI Generator 是 Swagger Codegen 的一个分支，2018年开始独立发展。主要优势包括:

- 更活跃的社区维护
- 更广泛的模板支持
- 更好的OpenAPI 3.0支持
- 更多的配置选项和自定义能力

安装OpenAPI Generator:

```text
# 使用npm安装
npm install @openapitools/openapi-generator-cli -g

# 使用Homebrew安装
brew install openapi-generator

# 下载JAR文件
wget https://repo1.maven.org/maven2/org/openapitools/openapi-generator-cli/6.0.1/openapi-generator-cli-6.0.1.jar -O openapi-generator-cli.jar
```


### 安装与基础使用

基本使用方法:

```text
# 显示帮助信息
openapi-generator help

# 生成Java客户端
openapi-generator generate \
  -i https://petstore.swagger.io/v2/swagger.json \
  -g java \
  -o ./java-client

# 列出支持的生成器
openapi-generator list
```


### 自定义模板

OpenAPI Generator 使用 Mustache 模板引擎。要自定义生成的代码，你需要:

- 获取默认模板
- 修改模板以满足需求
- 使用自定义模板生成代码

```text
# 使用JAR文件获取特定语言的模板
java -jar openapi-generator-cli.jar author template \
  -g java \
  -o ./custom-templates/java
```

模板文件示例 (Java 的 api.mustache):

```text
{{>licenseInfo}}
package {{package}};

{{#imports}}import {{import}};
{{/imports}}

{{#operations}}
public interface {{classname}} {
    {{#operation}}
    {{#summary}}
    /**
     * {{summary}}
     * {{/summary}}
     {{#notes}}
     * {{notes}}
     {{/notes}}
     */
    {{#returnType}}{{returnType}} {{/returnType}}{{^returnType}}void {{/returnType}}{{operationId}}({{#allParams}}{{dataType}} {{paramName}}{{^-last}}, {{/-last}}{{/allParams}});

    {{/operation}}
}
{{/operations}}
```

使用自定义模板生成代码:

```text
openapi-generator generate \
  -i https://petstore.swagger.io/v2/swagger.json \
  -g java \
  -o ./java-client-custom \
  -t ./custom-templates/java
```


### 自定义配置

OpenAPI Generator支持多种全局配置选项:

```text
openapi-generator generate \
  -i spec.yaml \
  -g java \
  -o output \
  --api-package com.example.api \
  --model-package com.example.model \
  --package-name com.example \
  --git-repo-id my-repo \
  --git-user-id my-username
```

不同的生成器有各自特定的配置选项:

```text
# Java客户端生成器的特定选项
openapi-generator generate \
  -i spec.yaml \
  -g java \
  -o output \
  --library retrofit2 \
  --java8 true \
  --use-rx-java true
```

可以创建配置文件保存常用设置:


## config.json 文件

使用配置文件:

```text
openapi-generator generate \
  -i spec.yaml \
  -g java \
  -o output \
  -c config.json
```


## 实战项目案例


### 从零开始的 API 设计

使用 Swagger Editor 设计 API:

- 访问 https://editor.swagger.io/
- 创建 OpenAPI 规范文件:


## 实例


### 完整项目代码生成

从设计的 API 规范生成完整项目:

- 保存 API 规范为 product-api.yaml
- 生成前后端代码:

```text
# 生成Spring Boot服务端
openapi-generator generate \
  -i product-api.yaml \
  -g spring \
  -o ./product-service \
  --additional-properties=java8=true,dateLibrary=java8

# 生成React前端
openapi-generator generate \
  -i product-api.yaml \
  -g typescript-fetch \
  -o ./product-frontend \
  --additional-properties=supportsES6=true,npmName=product-api-client
```


## 常见问题与解决方案

- 生成的代码无法编译 确保OpenAPI规范符合标准 检查自定义模板语法错误 更新到最新版本的生成器
- 自定义模板不生效 确保模板路径正确 检查模板文件名与原始模板相匹配 使用绝对路径而不是相对路径
- 生成的代码缺少某些功能 检查OpenAPI规范是否完整定义了所需功能 确认使用了正确的生成器和配置选项 考虑使用自定义模板添加额外功能
- 生成的代码与现有项目不兼容 使用配置选项调整包名和命名约定 通过自定义模板调整代码风格 考虑仅生成API接口，手动实现具体逻辑


## 高级功能与最佳实践


### 版本管理

管理 API 版本的最佳实践:

- 在 OpenAPI 规范中明确版本号
- 使用语义版本控制(SemVer)
- 为不同版本的 API 使用不同的基础路径
- 保存所有版本的规范文件


### CI/CD 集成

将代码生成集成到 CI/CD 流程:


## 实例


### 企业级应用建议

对于企业级项目:

- 集中管理API规范 使用Git存储库专门管理API规范 实施代码审查流程确保质量
- 建立生成代码的风格指南 创建一致的命名约定 制定错误处理标准 设计统一的认证处理方式
- 混合使用生成代码和手写代码 生成基础框架和数据模型 手动实现复杂业务逻辑 使用适配器模式隔离生成代码和手写代码
- 考虑微服务架构 为每个微服务维护独立的API规范 使用API网关统一对外接口 通过代码生成实现服务间的客户端


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Swagger Codegen` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
