# RESTful API：RESTful API 实际应用

- 来源：[RESTful API 实际应用](https://www.runoob.com/restfulapi/restful-api-application.html)
- 分类：后端开发
- 技术：RESTful API
- 笔记类型：学习笔记
- 章节序号：1136

## 本章内容

## 用户管理 API 设计

让我们设计一个完整的用户管理系统 API，这是最常见的应用场景。


### API 端点设计

```text
// 用户相关操作
GET    /api/users           # 获取用户列表
GET    /api/users/{id}      # 获取特定用户
POST   /api/users           # 创建新用户
PUT    /api/users/{id}      # 更新用户信息
DELETE /api/users/{id}      # 删除用户

// 用户订单相关操作
GET    /api/users/{id}/orders     # 获取用户的订单列表
POST   /api/users/{id}/orders     # 为用户创建订单
GET    /api/orders/{orderId}      # 获取特定订单详情
```


## 完整的 CRUD 操作


### 1. 创建用户（Create）

```text
// 请求
POST /api/users
Content-Type: application/json

{
  "name": "王五",
  "email": "wangwu@example.com",
  "phone": "13800000000",
  "address": {
    "city": "上海",
    "street": "南京路100号"
  }
}

// 成功响应（状态码：201 Created）
{
  "success": true,
  "data": {
    "id": 125,
    "name": "王五",
    "email": "wangwu@example.com",
    "phone": "13800000000",
    "address": {
      "city": "上海",
      "street": "南京路100号"
    },
    "createdAt": "2024-01-15T10:00:00Z",
    "updatedAt": "2024-01-15T10:00:00Z"
  },
  "message": "用户创建成功"
}
```


### 2. 读取用户（Read）

```text
// 获取用户列表
GET /api/users?page=1&limit=5&sort=createdAt&order=desc

// 响应（状态码：200 OK）
{
  "success": true,
  "data": [
    {
      "id": 125,
      "name": "王五",
      "email": "wangwu@example.com",
      "createdAt": "2024-01-15T10:00:00Z"
    },
    {
      "id": 124,
      "name": "李四",
      "email": "lisi@example.com",
      "createdAt": "2024-01-15T09:00:00Z"
    }
  ],
  "pagination": {
    "currentPage": 1,
    "totalPages": 3,
    "totalItems": 15,
    "itemsPerPage": 5
  }
}

// 获取特定用户
GET /api/users/125

// 响应
{
  "success": true,
  "data": {
    "id": 125,
    "name": "王五",
    "email": "wangwu@example.com",
    "phone": "13800000000",
    "address": {
      "city": "上海",
      "street": "南京路100号"
    },
    "createdAt": "2024-01-15T10:00:00Z",
    "updatedAt": "2024-01-15T10:00:00Z"
  }
}
```


### 3. 更新用户（Update）

```text
// 请求
PUT /api/users/125
Content-Type: application/json

{
  "name": "王五",
  "email": "wangwu.new@example.com",
  "phone": "13900000000",
  "address": {
    "city": "深圳",
    "street": "科技园路200号"
  }
}

// 响应（状态码：200 OK）
{
  "success": true,
  "data": {
    "id": 125,
    "name": "王五",
    "email": "wangwu.new@example.com",
    "phone": "13900000000",
    "address": {
      "city": "深圳",
      "street": "科技园路200号"
    },
    "createdAt": "2024-01-15T10:00:00Z",
    "updatedAt": "2024-01-15T11:30:00Z"
  },
  "message": "用户信息更新成功"
}
```


### 4. 删除用户（Delete）

```text
// 请求
DELETE /api/users/125

// 响应（状态码：200 OK）
{
  "success": true,
  "message": "用户删除成功"
}

// 如果用户不存在（状态码：404 Not Found）
{
  "success": false,
  "error": {
    "code": "USER_NOT_FOUND",
    "message": "用户不存在"
  }
}
```


## 错误处理


### 数据验证错误

```text
// 请求（邮箱格式错误）
POST /api/users
{
  "name": "",
  "email": "invalid-email",
  "phone": "123"
}

// 响应（状态码：400 Bad Request）
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "数据验证失败",
    "details": [
      {
        "field": "name",
        "message": "姓名不能为空"
      },
      {
        "field": "email",
        "message": "邮箱格式不正确"
      },
      {
        "field": "phone",
        "message": "手机号格式不正确"
      }
    ]
  }
}
```


### 资源不存在错误

```text
// 请求
GET /api/users/999

// 响应（状态码：404 Not Found）
{
  "success": false,
  "error": {
    "code": "USER_NOT_FOUND",
    "message": "用户不存在"
  }
}
```


## 使用 JavaScript 调用 API


## 实例


## 复习重点

- 能说明 `RESTful API 实际应用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
