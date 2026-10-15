# FastAPI：FastAPI CORS 跨域

- 来源：[FastAPI CORS 跨域](https://www.runoob.com/fastapi/fastapi-cors.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3859

## 本章内容

CORS（Cross-Origin Resource Sharing，跨域资源共享）是一种安全机制，允许或限制网页从不同域名请求资源。当前后端分离开发时，前端页面通常运行在不同的域名或端口上，需要配置 CORS 才能正常访问后端 API。


## 什么是跨域问题

浏览器的同源策略限制了网页向不同域名发送请求。例如：

同源的三要素：协议、域名、端口，任一不同即为跨域。


## 配置 CORS

FastAPI 使用 Starlette 的 CORSMiddleware 来处理跨域：


## 实例


## CORS 配置参数详解

allow_origins 使用 ["*"] 表示允许所有源，但这与 allow_credentials=True 不兼容。如果需要携带 Cookie，必须指定具体的源。


## 开发环境 vs 生产环境


### 开发环境

开发时为了方便，可以允许所有源：


## 实例


### 生产环境

生产环境必须指定具体的源：


## 实例

在生产环境中使用 allow_origins=["*"] 是安全隐患，可能导致跨站请求伪造（CSRF）攻击。务必指定具体的前端域名。


## CORS 预检请求

浏览器在发送某些跨域请求前，会先发送一个 OPTIONS 预检请求（preflight request），询问服务器是否允许实际请求。CORS 中间件会自动处理预检请求。

需要预检的请求条件：

- 使用了 PUT、DELETE 等非简单方法
- 请求头包含自定义字段（如 Authorization）
- Content-Type 不是 application/x-www-form-urlencoded、multipart/form-data 或 text/plain

设置了 max_age 后，浏览器会缓存预检结果，在指定时间内不会重复发送预检请求，减少网络开销。


## 小结

- CORS 是浏览器安全机制，前后端分离开发时必须配置
- 使用 CORSMiddleware 处理跨域请求
- 生产环境务必指定具体的 allow_origins，不要使用 ["*"]
- allow_credentials=True 与 allow_origins=["*"] 不兼容
- CORS 中间件自动处理浏览器的 OPTIONS 预检请求


## 复习重点

- 能说明 `FastAPI CORS 跨域` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
