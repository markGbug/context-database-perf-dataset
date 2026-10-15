# 知识点 18467：Flask：Flask Stream Helpers API - 两种用法

- 来源：[Flask Stream Helpers API](https://www.runoob.com/flask/flask-stream-helpers-api.html)
- 来源章节：[3910-flask-stream-helpers-api-practice.md](../chapters/3910-flask-stream-helpers-api-practice.md)
- 分类：Python / 数据科学
- 技术：Flask
- 所在小节：两种用法
- 知识类型：解释
- 原章节序号：3910

## 原文片段

注意事项：一旦响应体开始发送，就不能再修改响应头。如果生成器中需要访问 session，必须在视图函数中先访问 session 以触发 Vary: Cookie 头的设置。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `两种用法` 这一小节和 `Flask Stream Helpers API` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
