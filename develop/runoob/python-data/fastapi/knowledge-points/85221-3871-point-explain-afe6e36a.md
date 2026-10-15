# 知识点 85221：FastAPI：用户系统 - 实例

- 来源：[用户系统](https://www.runoob.com/fastapi/fastapi-blog-jwt-auth.html)
- 来源章节：[3871-fastapi-blog-jwt-auth-practice.md](../chapters/3871-fastapi-blog-jwt-auth-practice.md)
- 分类：Python / 数据科学
- 技术：FastAPI
- 所在小节：实例
- 知识类型：解释
- 原章节序号：3871

## 原文片段

JWT Token 中 sub 是标准的 subject 字段，存储用户标识。Token 本身不加密（只是 Base64 编码），所以绝对不能在里面放密码等敏感信息。如果你想加密，用 JWE 而非 JWT。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `实例` 这一小节和 `用户系统` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
