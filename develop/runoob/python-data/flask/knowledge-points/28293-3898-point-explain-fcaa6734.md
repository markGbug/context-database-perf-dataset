# 知识点 28293：Flask：Flask Request API - 获取请求数据

- 来源：[Flask Request API](https://www.runoob.com/flask/flask-request-api.html)
- 来源章节：[3898-flask-request-api-practice.md](../chapters/3898-flask-request-api-practice.md)
- 分类：Python / 数据科学
- 技术：Flask
- 所在小节：获取请求数据
- 知识类型：解释
- 原章节序号：3898

## 原文片段

对 args、form 等 MultiDict 类型，始终使用 .get(key, default) 方法获取值。直接用 request.args["key"] 访问不存在的键会抛出 KeyError（返回 400 错误）。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `获取请求数据` 这一小节和 `Flask Request API` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
