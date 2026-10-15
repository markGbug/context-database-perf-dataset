# 知识点 47841：FastAPI：FastAPI 静态文件 - 实例

- 来源：[FastAPI 静态文件](https://www.runoob.com/fastapi/fastapi-static-files.html)
- 来源章节：[3860-fastapi-static-files-study.md](../chapters/3860-fastapi-static-files-study.md)
- 分类：Python / 数据科学
- 技术：FastAPI
- 所在小节：实例
- 知识类型：解释
- 原章节序号：3860

## 原文片段

mount 是将一个独立的"子应用"挂载到指定路径上。StaticFiles 本身就是一个 ASGI 应用，它负责处理静态文件请求。挂载后，所有以 /static 开头的请求都由 StaticFiles 处理，不会经过 FastAPI 的路由系统。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `实例` 这一小节和 `FastAPI 静态文件` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
