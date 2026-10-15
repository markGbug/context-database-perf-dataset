# 知识点 71067：RESTful API：RESTful API 实践 - 统一错误格式

- 来源：[RESTful API 实践](https://www.runoob.com/restfulapi/restful-api-practices.html)
- 来源章节：[1137-restful-api-practices-study.md](../chapters/1137-restful-api-practices-study.md)
- 分类：后端开发
- 技术：RESTful API
- 所在小节：统一错误格式
- 知识类型：代码
- 原章节序号：1137

## 原文片段

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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `统一错误格式` 这一小节和 `RESTful API 实践` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
