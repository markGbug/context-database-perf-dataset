# 知识点 66830：FastAPI：FastAPI 路径参数 - 数据转换

- 来源：[FastAPI 路径参数](https://www.runoob.com/fastapi/fastapi-path-params.html)
- 来源章节：[3847-fastapi-path-params-study.md](../chapters/3847-fastapi-path-params-study.md)
- 分类：Python / 数据科学
- 技术：FastAPI
- 所在小节：数据转换
- 知识类型：代码
- 原章节序号：3847

## 原文片段

```text
# 传入整数，正常工作
GET /items/3       -> {"item_id": 3}

# 传入非整数，返回校验错误
GET /items/foo     -> 错误：Input should be a valid integer

# 传入浮点数，同样报错
GET /items/4.2     -> 错误：Input should be a valid integer
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `数据转换` 这一小节和 `FastAPI 路径参数` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
