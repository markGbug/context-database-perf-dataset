# 知识点 61345：JSP：JSP Session - 隐藏表单域

- 来源：[JSP Session](https://www.runoob.com/jsp/jsp-session.html)
- 来源章节：[0950-jsp-session-practice.md](../chapters/0950-jsp-session-practice.md)
- 分类：后端开发
- 技术：JSP
- 所在小节：隐藏表单域
- 知识类型：解释
- 原章节序号：0950

## 原文片段

相比而言，重写URL是更好的方式来，就算浏览器不支持cookies也能工作，但缺点是您必须为每个URL动态指定session ID，就算这是个简单的HTML页面。session对象 除了以上几种方法外，JSP利用servlet提供的HttpSession接口来识别一个用户，存储这个用户的所有访问信息。默认情况下，JSP允许会话跟踪，一个新的HttpSession对象将会自动地为新的客户端实例化。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `隐藏表单域` 这一小节和 `JSP Session` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
