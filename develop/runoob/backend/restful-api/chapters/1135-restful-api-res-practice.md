# RESTful API：RESTful API 请求和响应格式

- 来源：[RESTful API 请求和响应](https://www.runoob.com/restfulapi/restful-api-res.html)
- 分类：后端开发
- 技术：RESTful API
- 笔记类型：练习笔记
- 章节序号：1135

## 本章内容

## JSON 格式

现代 RESTful API 主要使用 JSON（JavaScript Object Notation）格式来传输数据。

JSON 就像是数据的"通用语言"，简单易读。


### JSON 基础语法

```text
{
  "name": "张三",
  "age": 25,
  "email": "zhangsan@example.com",
  "hobbies": ["阅读", "游泳", "编程"],
  "address": {
    "city": "北京",
    "district": "朝阳区"
  },
  "isActive": true
}
```


### 请求格式

GET 请求示例:

```text
// 请求
GET /api/users/123
Accept: application/json

// 响应
{
  "id": 123,
  "name": "张三",
  "email": "zhangsan@example.com",
  "createdAt": "2024-01-15T08:30:00Z"
}
```

POST 请求示例:

```text
// 请求
POST /api/users
Content-Type: application/json

{
  "name": "李四",
  "email": "lisi@example.com",
  "password": "securePassword123"
}

// 响应
{
  "id": 124,
  "name": "李四",
  "email": "lisi@example.com",
  "createdAt": "2024-01-15T09:00:00Z",
  "message": "用户创建成功"
}
```


## 响应结构设计


### 统一的响应格式

```text
{
  "success": true,
  "data": {
    "id": 123,
    "name": "张三"
  },
  "message": "操作成功",
  "timestamp": "2024-01-15T08:30:00Z"
}
```


### 错误响应格式

```text
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "输入数据验证失败",
    "details": [
      {
        "field": "email",
        "message": "邮箱格式不正确"
      }
    ]
  },
  "timestamp": "2024-01-15T08:30:00Z"
}
```


### 分页响应

```text
{
  "success": true,
  "data": [
    {
      "id": 1,
      "name": "用户1"
    },
    {
      "id": 2,
      "name": "用户2"
    }
  ],
  "pagination": {
    "currentPage": 1,
    "totalPages": 10,
    "totalItems": 100,
    "itemsPerPage": 10
  }
}
```


### 请求头常用字段


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `RESTful API 请求和响应` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
