# FastAPI：FastAPI 安全认证

- 来源：[FastAPI 安全认证](https://www.runoob.com/fastapi/fastapi-security.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3861

## 本章内容

FastAPI 内置了多种安全工具，支持 OAuth2、JWT 令牌、API Key 等常见的认证和授权方式。本节介绍如何实现基于 OAuth2 + JWT 的用户认证。


## 安全认证概述

FastAPI 支持的安全方案：


## OAuth2 密码模式 + JWT

这是前后端分离应用中最常用的认证方案。流程：

- 客户端发送用户名和密码到 /token 端点
- 服务器验证凭据，返回 JWT 访问令牌
- 客户端在后续请求中携带令牌（Authorization: Bearer <token>）
- 服务器验证令牌，识别用户身份


### 1. 安装依赖

```text
pip install "python-jose[cryptography]" passlib[bcrypt]
```


### 2. 完整示例


## 实例


## 代码解析


### 密码哈希

使用 passlib 的 bcrypt 算法对密码进行哈希处理，确保数据库中不存储明文密码：


### JWT 令牌

JWT（JSON Web Token）是一种安全的令牌格式，包含用户信息和过期时间：


### OAuth2PasswordBearer

告诉 FastAPI 从 Authorization: Bearer <token> 请求头中获取令牌：

```text
oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")
```

tokenUrl="token" 指定客户端获取令牌的端点路径，会出现在 API 文档中。

SECRET_KEY 必须保密且足够复杂，生产环境应使用环境变量存储。如果密钥泄露，攻击者可以伪造任意用户的令牌。


## 使用 API 文档测试

配置 OAuth2 后，Swagger UI 会出现"Authorize"按钮：

- 点击 "Authorize"
- 输入用户名和密码（如 alice / secret）
- 点击 "Authorize" 获取令牌
- 之后的所有请求都会自动携带令牌


## 小结

- OAuth2 + JWT 是前后端分离应用最常用的认证方案
- 密码必须哈希存储，不能明文保存
- JWT 令牌包含用户标识和过期时间
- 使用依赖注入（Depends）实现认证逻辑的复用
- 生产环境中 SECRET_KEY 必须保密


## 复习重点

- 能说明 `FastAPI 安全认证` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
