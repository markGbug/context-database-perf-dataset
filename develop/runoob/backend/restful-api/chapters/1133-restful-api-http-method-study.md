# RESTful API：HTTP 方法

- 来源：[HTTP 方法](https://www.runoob.com/restfulapi/restful-api-http-method.html)
- 分类：后端开发
- 技术：RESTful API
- 笔记类型：学习笔记
- 章节序号：1133

## 本章内容

## HTTP 方法

HTTP 方法就像是你对数据的"动作指令"。

在 RESTful API 中，我们主要使用四种方法，它们对应数据的四种基本操作：


### GET 方法

GET 用于获取数据，就像你问服务员"今天有什么菜？"

```text
// 获取所有用户
GET /api/users

// 获取特定用户
GET /api/users/123

// 获取用户的订单
GET /api/users/123/orders
```

特点：

- 安全操作，不会修改数据
- 可以被缓存
- 参数放在 URL 中


### POST 方法

POST 用于创建新数据，就像你告诉服务员"我要点一份宫保鸡丁"

```text
// 创建新用户
POST /api/users
{
  "name": "张三",
  "email": "zhangsan@example.com"
}

// 创建新订单
POST /api/orders
{
  "userId": 123,
  "items": ["商品A", "商品B"]
}
```

特点：

- 会修改服务器状态
- 不是幂等的（多次调用会创建多个资源）
- 数据放在请求体中


### PUT 方法

PUT 用于更新整个资源，就像你说"把我的订单改成这样"

```text
// 更新用户信息
PUT /api/users/123
{
  "name": "李四",
  "email": "lisi@example.com",
  "phone": "13800138000"
}
```

特点：

- 是幂等的（多次调用结果相同）
- 通常替换整个资源
- 如果资源不存在，可能会创建新资源


### DELETE 方法

DELETE 用于删除资源，就像你说"取消我的订单"

```text
// 删除用户
DELETE /api/users/123

// 删除订单
DELETE /api/orders/456
```

- 是幂等的
- 删除指定资源
- 成功后资源不再存在


### HTTP 状态码

当服务器处理完请求后，会返回状态码告诉你结果：


## 复习重点

- 能说明 `HTTP 方法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
