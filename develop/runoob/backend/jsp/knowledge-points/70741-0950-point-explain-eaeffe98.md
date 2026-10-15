# 知识点 70741：JSP：JSP Session - 隐藏表单域

- 来源：[JSP Session](https://www.runoob.com/jsp/jsp-session.html)
- 来源章节：[0950-jsp-session-study.md](../chapters/0950-jsp-session-study.md)
- 分类：后端开发
- 技术：JSP
- 所在小节：隐藏表单域
- 知识类型：解释
- 原章节序号：0950

## 原文片段

禁止会话跟踪需要显式地关掉它，通过将page指令中session属性值设为false来实现，就像下面这样： <%@ page session="false" %> JSP引擎将隐含的session对象暴露给开发者。由于提供了session对象，开发者就可以方便地存储或检索数据。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `隐藏表单域` 这一小节和 `JSP Session` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
