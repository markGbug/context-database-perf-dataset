# 知识点 12926：RESTful API：RESTful API 进阶 - JWT (JSON Web Token) 认证

- 来源：[RESTful API 进阶](https://www.runoob.com/restfulapi/restful-api-advance.html)
- 来源章节：[1139-restful-api-advance-study.md](../chapters/1139-restful-api-advance-study.md)
- 分类：后端开发
- 技术：RESTful API
- 所在小节：JWT (JSON Web Token) 认证
- 知识类型：代码
- 原章节序号：1139

## 原文片段

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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `JWT (JSON Web Token) 认证` 这一小节和 `RESTful API 进阶` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
