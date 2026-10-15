# Swagger：Swagger 实战教程：图书管理 API

- 来源：[Swagger 实战教程](https://www.runoob.com/swagger/swagger-practice.html)
- 分类：后端开发
- 技术：Swagger
- 笔记类型：练习笔记
- 章节序号：1205

## 本章内容

本教程将带您实现一个基于Swagger的图书管理系统API，主要功能包括：

- 图书的增删改查操作
- 分页查询
- 条件过滤
- API文档自动生成
- 在线接口测试

技术栈：

- Node.js + Express
- Swagger UI Express
- Swagger JSDoc


## 环境准备


### 安装Node.js

确保您的系统已安装 Node.js（建议使用v14.0.0或更高版本）。


### 检查环境

```text
node -v
npm -v
```


## 项目初始化


### 创建项目目录

```text
mkdir book-management-api
cd book-management-api
npm init -y
```


### 安装依赖包

```text
npm install express cors swagger-ui-express swagger-jsdoc nodemon --save
```


### 创建基础项目结构

```text
book-management-api/
├── node_modules/
├── models/
│   └── book.js
├── routes/
│   └── books.js
├── middleware/
│   └── auth.js
├── swagger/
│   └── swagger.js
├── app.js
└── package.json
```


### 创建入口文件 app.js


## 实例


## API 设计与实现


### 创建图书模型

在models/book.js 中创建一个简单的内存数据模型：


## 实例


### 实现路由控制器

在 routes/books.js 中实现 API 路由：


## 实例


## Swagger 文档配置


### 配置 Swagger

创建 swagger/swagger.js 文件：


## 实例


### 添加认证中间件

创建 middleware/auth.js：


## 实例


## 接口功能测试


### 启动服务

使用以下命令启动服务：

```text
# 如果已配置了package.json中的scripts，执行：
npm start

# 或者直接使用nodemon
npx nodemon app.js
```


### 6.2 访问Swagger文档

打开浏览器访问： http://localhost:3000/api-docs


### 使用 Swagger 测试接口

- 获取所有图书 点击 GET /api/books 接口 点击 "Try it out" 按钮 可以设置分页参数 page 和 limit，以及过滤条件 点击 "Execute" 按钮发送请求 观察结果
- 创建新图书 点击 POST /api/books 接口 点击 "Try it out" 按钮 在请求体中填入图书信息，例如： { "title": "RESTful API设计", "author": "Martin Fowler", "publishDate": "2020-01-01", "isbn": "978-1234567890", "category": "编程" } 点击 "Execute" 按钮发送请求 观察结果
- 获取、更新和删除 使用类似方法测试其他接口


## 常见问题排查


## 后续章节

- 跨域问题
- 实例
- 认证配置错误
- Swagger 文档不更新
- 进阶功能
- 添加 API 版本控制
- 添加请求验证
- 实例
- 添加响应压缩
- 添加响应缓存
- 添加请求限流

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Swagger 实战教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
