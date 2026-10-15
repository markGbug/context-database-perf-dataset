# 知识点 85197：FastAPI：FastAPI CORS 跨域 - CORS 预检请求

- 来源：[FastAPI CORS 跨域](https://www.runoob.com/fastapi/fastapi-cors.html)
- 来源章节：[3859-fastapi-cors-practice.md](../chapters/3859-fastapi-cors-practice.md)
- 分类：Python / 数据科学
- 技术：FastAPI
- 所在小节：CORS 预检请求
- 知识类型：解释
- 原章节序号：3859

## 原文片段

浏览器在发送某些跨域请求前，会先发送一个 OPTIONS 预检请求（preflight request），询问服务器是否允许实际请求。CORS 中间件会自动处理预检请求。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `CORS 预检请求` 这一小节和 `FastAPI CORS 跨域` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
