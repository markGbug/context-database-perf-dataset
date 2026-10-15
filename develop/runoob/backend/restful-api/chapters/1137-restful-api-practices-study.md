# RESTful API：RESTful API 实践

- 来源：[RESTful API 实践](https://www.runoob.com/restfulapi/restful-api-practices.html)
- 分类：后端开发
- 技术：RESTful API
- 笔记类型：学习笔记
- 章节序号：1137

## 本章内容

## 安全性最佳实践


### 1. 身份验证和授权

```text
// 使用 JWT Token 进行身份验证
GET /api/users/profile
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...

// API 响应包含用户权限检查
{
  "success": true,
  "data": {
    "id": 123,
    "name": "张三",
    "role": "user"
  }
}
```


### 2. 输入验证

```text
// 服务器端验证示例
POST /api/users
{
  "email": "test@example.com",
  "password": "123"  // 密码太短
}

// 验证失败响应
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "密码长度至少为8位"
  }
}
```


### 3. HTTPS 和数据加密

- ✅ https://api.example.com/users
- ❌ http://api.example.com/users


## 性能优化实践


### 1. 数据分页

```text
// 避免一次返回大量数据
GET /api/users?page=1&limit=20

{
  "success": true,
  "data": [...], // 只返回20条记录
  "pagination": {
    "currentPage": 1,
    "totalPages": 50,
    "totalItems": 1000
  }
}
```


### 2. 字段过滤

```text
// 只返回需要的字段
GET /api/users?fields=id,name,email

{
  "success": true,
  "data": [
    {
      "id": 1,
      "name": "张三",
      "email": "zhangsan@example.com"
      // 不返回其他不需要的字段
    }
  ]
}
```


### 3. 缓存策略

```text
// 使用缓存头
GET /api/users/123
Cache-Control: max-age=3600  // 缓存1小时

// 条件请求
GET /api/users/123
If-None-Match: "etag-value"

// 304 Not Modified (数据未变化)
```


## 错误处理最佳实践


### 统一错误格式

```text
{
  "success": false,
  "error": {
    "code": "SPECIFIC_ERROR_CODE",    // 机器可读的错误码
    "message": "用户友好的错误信息",      // 人类可读的错误信息
    "details": {...},                // 详细错误信息（可选）
    "timestamp": "2024-01-15T10:00:00Z"
  }
}
```


### 常见错误码设计

```javascript
const ERROR_CODES = {
  // 4xx 客户端错误
  'VALIDATION_ERROR': 400,        // 数据验证失败
  'UNAUTHORIZED': 401,            // 未授权
  'FORBIDDEN': 403,              // 禁止访问
  'NOT_FOUND': 404,              // 资源不存在
  'METHOD_NOT_ALLOWED': 405,     // 方法不允许
  'CONFLICT': 409,               // 资源冲突

  // 5xx 服务器错误
  'INTERNAL_ERROR': 500,         // 内部服务器错误
  'SERVICE_UNAVAILABLE': 503     // 服务不可用
}
```


## API 文档化


### 使用标准化文档格式

推荐使用 OpenAPI (Swagger) 规范：

```text
# swagger.yaml 示例
openapi: 3.0.0
info:
  title: 用户管理 API
  version: 1.0.0
  description: 提供用户的增删改查功能

paths:
  /api/users:
    get:
      summary: 获取用户列表
      parameters:
        - name: page
          in: query
          description: 页码
          schema:
            type: integer
            default: 1
      responses:
        '200':
          description: 成功
          content:
            application/json:
              schema:
                type: object
                properties:
                  success:
                    type: boolean
                  data:
                    type: array
                    items:
                      $ref: '#/components/schemas/User'
```


## 版本控制策略


### URL 版本控制（推荐）

```text
// 版本1
GET /api/v1/users

// 版本2（新增字段，保持向后兼容）
GET /api/v2/users
{
  "id": 1,
  "name": "张三",
  "email": "zhangsan@example.com",
  "avatar": "https://example.com/avatar.jpg"  // 新增字段
}
```


### 兼容性处理

```text
// 保持向后兼容的策略
{
  "deprecationWarning": "该 API 版本将在2024年6月1日后停止支持，请升级到 v2",
  "data": {...}
}
```


## 实践练习


### 练习一：图书管理系统 API

设计一个简单的图书管理系统，包含以下功能：

- 管理图书信息（标题、作者、ISBN、价格）
- 管理图书分类
- 支持图书的增删改查
- 支持按分类筛选图书

请设计以下 API 端点：

```text
// 你的任务：完善以下 API 设计

// 图书相关
GET    /api/books                    // 获取图书列表
GET    /api/books/{id}              // 获取特定图书
POST   /api/books                   // 创建新图书
PUT    /api/books/{id}              // 更新图书信息
DELETE /api/books/{id}              // 删除图书

// 分类相关
GET    /api/categories              // 获取分类列表
GET    /api/categories/{id}/books   // 获取分类下的图书
```

示例数据结构：

```text
{
  "id": 1,
  "title": "JavaScript 高级程序设计",
  "author": "Nicholas C. Zakas",
  "isbn": "9787115275790",
  "price": 99.00,
  "categoryId": 1,
  "category": {
    "id": 1,
    "name": "编程技术"
  },
  "publishedDate": "2012-03-01",
  "description": "深入理解JavaScript语言",
  "stock": 50
}
```

- 设计 API 文档：为每个端点编写详细的请求和响应示例
- 错误处理：设计各种错误情况的响应格式
- 数据验证：列出每个字段的验证规则
- 测试用例：编写测试每个 API 的 curl 命令


### 练习二：待办事项 API

创建一个待办事项管理 API：

- 创建、查看、更新、删除待办事项
- 标记任务完成状态
- 按状态筛选任务
- 支持任务优先级

```text
{
  "id": 1,
  "title": "学习 RESTful API",
  "description": "完成 API 教程的学习",
  "status": "pending",  // pending, completed, cancelled
  "priority": "high",   // low, medium, high
  "dueDate": "2024-01-20",
  "createdAt": "2024-01-15T08:00:00Z",
  "updatedAt": "2024-01-15T08:00:00Z"
}
```

- 批量操作：设计批量更新任务状态的 API
- 搜索功能：支持按标题和描述搜索
- 统计信息：返回任务完成情况的统计数据


### 练习三：社交媒体 API

设计一个简化版社交媒体平台的 API：

- 用户注册和登录
- 发布和查看动态
- 关注其他用户
- 点赞和评论

```text
// 用户相关
POST /api/auth/register     // 用户注册
POST /api/auth/login        // 用户登录
GET  /api/users/profile     // 获取个人资料

// 动态相关
GET  /api/posts            // 获取动态列表
POST /api/posts            // 发布新动态
GET  /api/posts/{id}       // 获取特定动态
DELETE /api/posts/{id}     // 删除动态

// 互动相关
POST /api/posts/{id}/like     // 点赞动态
POST /api/posts/{id}/comments // 添加评论
GET  /api/posts/{id}/comments // 获取评论列表
```

- 关注系统：用户之间的关注关系
- 消息推送：新互动的通知机制
- 内容审核：敏感内容的过滤


## 复习重点

- 能说明 `RESTful API 实践` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
