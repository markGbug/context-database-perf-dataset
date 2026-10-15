# FastAPI：FastAPI 响应模型

- 来源：[FastAPI 响应模型](https://www.runoob.com/fastapi/fastapi-response-model.html)
- 分类：Python / 数据科学
- 技术：FastAPI
- 笔记类型：学习笔记
- 章节序号：3853

## 本章内容

响应模型用于声明 API 返回的数据结构。通过声明响应模型，FastAPI 会自动完成输出数据的校验、序列化和过滤，确保客户端只接收到预期的数据。


## 使用返回类型注解

最简单的方式是直接注解路径操作函数的返回类型：


## 实例

FastAPI 使用响应模型完成以下工作：


## response_model 参数

当返回类型与响应模型不一致时，使用装饰器的 response_model 参数：


## 实例

这是保护敏感数据的重要手段。使用不同的输入和输出模型，确保密码等敏感字段永远不会出现在 API 响应中。


## 返回类型与数据过滤

推荐使用类继承来实现输入/输出模型的分离，这样既能让编辑器和 mypy 正确理解类型，又能让 FastAPI 过滤数据：


## 实例


## 排除未设置的默认值

使用 response_model_exclude_unset=True，只返回实际设置了值的字段：


## 实例

不同 item_id 的响应对比：

相关的过滤参数：


## 包含/排除特定字段

使用 response_model_include 和 response_model_exclude 精确控制输出字段：


## 实例

虽然 response_model_include 和 response_model_exclude 可以快速过滤字段，但推荐使用多个模型类来代替，因为它们无法从 OpenAPI 文档中移除被排除的字段。


## 小结

- 使用 response_model 参数或返回类型注解声明响应模型
- 响应模型的核心作用是数据过滤，保护敏感数据不被泄露
- 为输入和输出使用不同的模型，确保密码等字段不会出现在响应中
- response_model_exclude_unset 只返回实际设置的字段
- 推荐使用模型继承 + 返回类型注解，而非 response_model_include/exclude


## 复习重点

- 能说明 `FastAPI 响应模型` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
