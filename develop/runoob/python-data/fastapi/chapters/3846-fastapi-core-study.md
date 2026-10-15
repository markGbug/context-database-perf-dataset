# FastAPI：FastAPI 核心概念

- 来源：[FastAPI 核心概念](https://www.runoob.com/fastapi/fastapi-core.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3846

## 本章内容

FastAPI 是一个现代、快速（高性能）的 Python Web 框架，用于构建 API。它基于标准 Python 类型提示，使用 Starlette 和 Pydantic 构建。


### 主要特点

- 高性能：与 NodeJS 和 Go 相当，是最快的 Python 框架之一
- 快速开发：开发速度提高约 200%-300%
- 减少错误：减少约 40% 的人为错误
- 直观：强大的编辑器支持，自动补全无处不在
- 简单：易于使用和学习，减少阅读文档的时间


## ASGI 与异步编程


### 什么是 ASGI？

ASGI（Asynchronous Server Gateway Interface）是 Python 异步 Web 服务器和应用程序之间的标准接口。

WSGI vs ASGI 对比：


## 实例


### 异步编程核心概念

同步 vs 异步执行：


## 实例

FastAPI 中的异步路径操作：


## 实例


### 何时使用异步？

适合异步的场景：

- 数据库操作
- 网络请求（API 调用）
- 文件 I/O 操作
- 长时间等待的操作

不适合异步的场景：

- CPU 密集型计算
- 简单的数据处理
- 没有 I/O 等待的操作


## 实例


## REST API 设计原则


### REST 基础概念

REST（Representational State Transfer）是一种 Web API 设计风格，强调：

- 资源导向：URL 表示资源
- 状态无关：每个请求都是独立的
- 统一接口：使用标准 HTTP 方法
- 分层系统：支持缓存、负载均衡等


### RESTful URL 设计

良好的 URL 设计示例：


## 实例

URL 设计原则：

```text
好的设计
GET    /api/v1/users              # 获取用户列表
GET    /api/v1/users/123          # 获取用户 123
POST   /api/v1/users              # 创建用户
GET    /api/v1/users/123/orders   # 获取用户 123 的订单

# 不好的设计
GET    /api/v1/getAllUsers        # 动词不应该在 URL 中
GET    /api/v1/user/123           # 集合名应该用复数
POST   /api/v1/createUser         # URL 中包含动作
GET    /api/v1/users-orders-123   # 关系不清晰
```


### 资源的层次关系


## 实例


## HTTP 方法与状态码


### HTTP 方法的语义


## 实例


### HTTP 状态码的使用


## 实例

常用状态码速查：

```text
# 成功状态码
200 OK                    # 请求成功
201 Created              # 资源创建成功
204 No Content           # 成功但无内容返回
206 Partial Content      # 部分内容（分页、断点续传）

# 重定向
301 Moved Permanently    # 永久重定向
302 Found               # 临时重定向
304 Not Modified        # 资源未修改（缓存）

# 客户端错误
400 Bad Request         # 请求格式错误
401 Unauthorized        # 未认证
403 Forbidden          # 已认证但无权限
404 Not Found          # 资源不存在
405 Method Not Allowed  # HTTP 方法不允许
409 Conflict           # 资源冲突
422 Unprocessable Entity # 数据验证失败
429 Too Many Requests   # 请求过于频繁

# 服务器错误
500 Internal Server Error # 服务器内部错误
502 Bad Gateway          # 网关错误
503 Service Unavailable  # 服务不可用
```


## JSON 数据格式


### JSON 基础与最佳实践


## 实例


### JSON Schema 与数据验证


## 后续章节

- 实例
- 错误响应格式
- 实例
- FastAPI 特有概念
- 自动文档生成
- 实例
- 依赖注入系统预览
- 实例
- 类型提示的重要性
- 实例
- 核心概念实践示例
- 实例

## 复习重点

- 能说明 `FastAPI 核心概念` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
