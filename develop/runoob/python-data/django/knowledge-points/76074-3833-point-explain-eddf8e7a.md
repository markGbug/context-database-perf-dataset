# 知识点 76074：Django：表单与收藏功能 - 实例

- 来源：[表单与收藏功能](https://www.runoob.com/django/django-blog-forms-favorites.html)
- 来源章节：[3833-django-blog-forms-favorites-practice.md](../chapters/3833-django-blog-forms-favorites-practice.md)
- 分类：Python / 数据科学
- 技术：Django
- 所在小节：实例
- 知识类型：解释
- 原章节序号：3833

## 原文片段

为什么收藏按钮用 form 而不是 a 标签？因为收藏操作修改了数据库，属于 POST 请求。按照 REST 规范，读操作用 GET，写操作用 POST。更重要的是，POST 请求携带 csrf_token，防止恶意网站伪造请求。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `实例` 这一小节和 `表单与收藏功能` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
