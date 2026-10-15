# 知识点 42089：JSP：JSP Session - 隐藏表单域

- 来源：[JSP Session](https://www.runoob.com/jsp/jsp-session.html)
- 来源章节：[0950-jsp-session-study.md](../chapters/0950-jsp-session-study.md)
- 分类：后端开发
- 技术：JSP
- 所在小节：隐藏表单域
- 知识类型：解释
- 原章节序号：0950

## 原文片段

一个网络服务器可以发送一个隐藏的HTML表单域和一个唯一的session ID，就像下面这样： <input type="hidden" name="sessionid" value="12345"> 这个条目意味着，当表单被提交时，指定的名称和值将会自动包含在GET或POST数据中。每当浏览器发送一个请求，session_id的值就可以用来保存不同浏览器的轨迹。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `隐藏表单域` 这一小节和 `JSP Session` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
