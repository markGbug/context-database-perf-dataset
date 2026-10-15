# RESTful API：RESTful API 测试和调试

- 来源：[RESTful API 调试](https://www.runoob.com/restfulapi/restful-api-debug.html)
- 分类：后端开发
- 技术：RESTful API
- 笔记类型：练习笔记
- 章节序号：1138

## 本章内容

## 使用工具测试 API


### 1. Postman 测试

Postman 是最流行的 API 测试工具，就像是 API 的"试验场"。

Postman 官网地址：https://www.postman.com/。

基本测试步骤：

- 创建新请求
- 设置 HTTP 方法（GET、POST 等）
- 输入 API 地址
- 添加请求头和请求体
- 发送请求查看响应

Postman 集合示例：

```text
{
  "info": {
    "name": "用户管理 API 测试",
    "description": "测试用户相关的所有 API 端点"
  },
  "item": [
    {
      "name": "获取用户列表",
      "request": {
        "method": "GET",
        "header": [],
        "url": {
          "raw": "{{baseUrl}}/api/users?page=1&limit=10",
          "host": ["{{baseUrl}}"],
          "path": ["api", "users"],
          "query": [
            {"key": "page", "value": "1"},
            {"key": "limit", "value": "10"}
          ]
        }
      }
    }
  ]
}
```


### 2. curl 命令行测试

```text
# 获取用户列表
curl -X GET "https://api.example.com/users" \
     -H "Content-Type: application/json"

# 创建新用户
curl -X POST "https://api.example.com/users" \
     -H "Content-Type: application/json" \
     -d '{
       "name": "张三",
       "email": "zhangsan@example.com"
     }'

# 更新用户信息
curl -X PUT "https://api.example.com/users/123" \
     -H "Content-Type: application/json" \
     -d '{
       "name": "李四",
       "email": "lisi@example.com"
     }'

# 删除用户
curl -X DELETE "https://api.example.com/users/123" \
     -H "Content-Type: application/json"
```


### 3. 浏览器开发者工具

```javascript
// 在浏览器控制台中测试
fetch('/api/users', {
  method: 'GET',
  headers: {
    'Content-Type': 'application/json'
  }
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error('Error:', error));
```


## 常见问题调试


### 1. CORS 跨域问题

报错信息：

```text
Access to fetch at 'https://api.example.com/users' from origin 'http://localhost:3000'
has been blocked by CORS policy
```

解决方案：

```text
// 服务器端需要设置 CORS 头
app.use((req, res, next) => {
  res.header('Access-Control-Allow-Origin', '*');
  res.header('Access-Control-Allow-Methods', 'GET,PUT,POST,DELETE');
  res.header('Access-Control-Allow-Headers', 'Content-Type, Authorization');
  next();
});
```


### 2. 状态码错误

常见错误及原因：


### 3. 数据格式问题

```text
// 错误的请求格式
{
  name: "张三",  // ❌ 缺少引号
  'email': "test@example.com",  // ❌ 单引号
  age: "25"  // ❌ 数字用了字符串
}

// 正确的请求格式
{
  "name": "张三",  // ✅ 双引号
  "email": "test@example.com",  // ✅ 双引号
  "age": 25  // ✅ 数字类型
}
```


## 自动化测试


### 单元测试示例


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `RESTful API 调试` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
