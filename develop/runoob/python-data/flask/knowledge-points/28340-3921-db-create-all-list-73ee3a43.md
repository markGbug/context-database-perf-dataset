# 知识点 28340：Flask：Flask-Migrate - 为什么不能一直用 db.create_all()？

- 来源：[Flask-Migrate](https://www.runoob.com/flask/flask-blog-migrate.html)
- 来源章节：[3921-flask-blog-migrate-study.md](../chapters/3921-flask-blog-migrate-study.md)
- 分类：Python / 数据科学
- 技术：Flask
- 所在小节：为什么不能一直用 db.create_all()？
- 知识类型：要点
- 原章节序号：3921

## 原文片段

只在表不存在时创建。修改模型（如新增字段），已存在的表不会更新

## 学习理解

这是一个列表型要点，通常用于总结特性、规则、组成部分或注意事项。复习时要把它放回本章上下文。

- 它属于哪一类规则或特性？
- 和同组其他要点有什么区别？
- 有没有可以补充的例子或反例？

## 复习问题

- `为什么不能一直用 db.create_all()？` 这一小节和 `Flask-Migrate` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
