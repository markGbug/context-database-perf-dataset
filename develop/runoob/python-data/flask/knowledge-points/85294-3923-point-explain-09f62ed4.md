# 知识点 85294：Flask：Flask-Login - 实例

- 来源：[Flask-Login](https://www.runoob.com/flask/flask-blog-login.html)
- 来源章节：[3923-flask-blog-login-study.md](../chapters/3923-flask-blog-login-study.md)
- 分类：Python / 数据科学
- 技术：Flask
- 所在小节：实例
- 知识类型：解释
- 原章节序号：3923

## 原文片段

永远不要明文存储密码！generate_password_hash() 使用 PBKDF2 算法对密码做 salted hash。即使数据库泄露，攻击者也无法反向推导密码。校验密码时用 check_password_hash()。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `实例` 这一小节和 `Flask-Login` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
