# RESTful API：URL 设计规范

- 来源：[RESTful URL](https://www.runoob.com/restfulapi/restful-api-url.html)
- 分类：后端开发
- 技术：RESTful API
- 笔记类型：练习笔记
- 章节序号：1134

## 本章内容

## 资源导向的 URL 设计

RESTful API 的 URL 应该表示"资源"而不是"动作"。

把 URL 想象成图书馆的书架标签，它告诉你在哪里能找到什么资源。


### 好的设计 ✅

```text
GET /api/users          # 获取所有用户
GET /api/users/123      # 获取 ID 为 123 的用户
POST /api/users         # 创建新用户
PUT /api/users/123      # 更新用户 123
DELETE /api/users/123   # 删除用户 123
```


### 不好的设计 ❌

```text
GET /api/getUsers       # 动词出现在 URL 中
POST /api/createUser    # 动作导向而非资源导向
GET /api/user/delete/123 # 混乱的结构
```


## URL 命名规范


### 使用名词而非动词

- ✅ GET /api/books
- ❌ GET /api/getBooks


### 使用复数形式

- ✅ GET /api/users
- ❌ GET /api/user


### 使用小写字母

- ✅ GET /api/user-orders
- ❌ GET /api/UserOrders


### 使用连字符分隔单词

- ✅ GET /api/user-profiles
- ❌ GET /api/user_profiles
- ❌ GET /api/userProfiles


## 嵌套资源

当资源之间有从属关系时，可以使用嵌套 URL：

```text
// 获取用户 123 的所有订单
GET /api/users/123/orders

// 获取用户 123 的订单 456
GET /api/users/123/orders/456

// 为用户 123 创建新订单
POST /api/users/123/orders
```


### 嵌套层级建议


## 查询参数

用于过滤、排序和分页：

```text
javascript// 分页
GET /api/users?page=1&limit=10

// 过滤
GET /api/users?status=active&city=beijing

// 排序
GET /api/users?sort=created_at&order=desc

// 搜索
GET /api/users?search=张三
```


## API 版本控制

为了保持向后兼容，API 需要版本控制：


### URL 路径版本控制

```text
GET /api/v1/users
GET /api/v2/users
```


### 请求头版本控制

```text
GET /api/users
Accept: application/vnd.api+json;version=1
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `RESTful URL` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
