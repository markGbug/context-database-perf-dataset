# 知识点 76233：Flask：打包上线 - 实例

- 来源：[打包上线](https://www.runoob.com/flask/flask-blog-deploy.html)
- 来源章节：[3926-flask-blog-deploy-study.md](../chapters/3926-flask-blog-deploy-study.md)
- 分类：Python / 数据科学
- 技术：Flask
- 所在小节：实例
- 知识类型：解释
- 原章节序号：3926

## 原文片段

注意 import 顺序：Blueprint 和 user_loader 必须在 create_app() 内部导入（而非文件顶部），否则会触发循环导入（Blueprint 引用了 models，models 引用了 db，而 db 此时尚未绑定到 app）。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `实例` 这一小节和 `打包上线` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
