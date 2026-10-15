# 知识点 80262：RESTful API：RESTful API 调试 - 1. Postman 测试

- 来源：[RESTful API 调试](https://www.runoob.com/restfulapi/restful-api-debug.html)
- 来源章节：[1138-restful-api-debug-study.md](../chapters/1138-restful-api-debug-study.md)
- 分类：后端开发
- 技术：RESTful API
- 所在小节：1. Postman 测试
- 知识类型：代码
- 原章节序号：1138

## 原文片段

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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `1. Postman 测试` 这一小节和 `RESTful API 调试` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
