# RESTful API：RESTful API 进阶

- 来源：[RESTful API 进阶](https://www.runoob.com/restfulapi/restful-api-advance.html)
- 分类：后端开发
- 技术：RESTful API
- 笔记类型：学习笔记
- 章节序号：1139

## 本章内容

## 认证和授权


### JWT (JSON Web Token) 认证

JWT 就像是一张"数字身份证"，包含了用户的身份信息，并且可以验证真伪。

```text
// JWT 的结构
// Header.Payload.Signature

// 登录流程
POST /api/auth/login
{
  "email": "user@example.com",
  "password": "password123"
}

// 响应
{
  "success": true,
  "data": {
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
    "user": {
      "id": 123,
      "name": "张三",
      "email": "user@example.com"
    }
  }
}

// 后续请求携带 Token
GET /api/users/profile
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```


### OAuth 2.0 集成

```text
// 第三方登录流程
GET /api/auth/google/redirect
// 重定向到 Google 授权页面

// 回调处理
GET /api/auth/google/callback?code=authorization_code
// 返回应用 Token
API 限流和配额
请求频率限制
javascript// 响应头中包含限流信息
HTTP/1.1 200 OK
X-RateLimit-Limit: 1000        // 每小时限制1000次请求
X-RateLimit-Remaining: 999     // 剩余请求次数
X-RateLimit-Reset: 1642694400  // 重置时间戳

// 超出限制时的响应
HTTP/1.1 429 Too Many Requests
{
  "success": false,
  "error": {
    "code": "RATE_LIMIT_EXCEEDED",
    "message": "请求过于频繁，请稍后再试",
    "retryAfter": 3600  // 建议等待时间（秒）
  }
}
```


## 数据缓存策略


### HTTP 缓存头

```text
// 设置缓存策略
GET /api/users/123
Cache-Control: public, max-age=3600  // 缓存1小时
ETag: "a1b2c3d4e5f6"                // 资源版本标识

// 条件请求
GET /api/users/123
If-None-Match: "a1b2c3d4e5f6"

// 如果资源未变化
HTTP/1.1 304 Not Modified
```


### Redis 缓存示例

```javascript
// 缓存策略伪代码
async function getUser(userId) {
  // 1. 先检查缓存
  const cached = await redis.get(`user:${userId}`);
  if (cached) {
    return JSON.parse(cached);
  }

  // 2. 缓存未命中，查询数据库
  const user = await database.findUser(userId);

  // 3. 将结果缓存
  await redis.setex(`user:${userId}`, 3600, JSON.stringify(user));

  return user;
}
```


## 微服务架构中的 API


### 服务间通信


### API 网关模式

```text
// API 网关路由配置
{
  "routes": [
    {
      "path": "/api/users/*",
      "service": "user-service",
      "url": "http://user-service:3001"
    },
    {
      "path": "/api/orders/*",
      "service": "order-service",
      "url": "http://order-service:3002"
    }
  ]
}
```


## GraphQL vs REST


### REST API 的局限性

```text
// REST: 需要多次请求获取相关数据
GET /api/users/123        // 获取用户信息
GET /api/users/123/posts  // 获取用户发布的文章
GET /api/posts/456/comments // 获取文章评论
```


### GraphQL 的优势

```text
// GraphQL: 一次请求获取所需数据
query {
  user(id: 123) {
    name
    email
    posts {
      title
      comments {
        content
        author
      }
    }
  }
}
```


## 复习重点

- 能说明 `RESTful API 进阶` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
