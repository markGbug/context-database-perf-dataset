# 知识点 88960：JSP：JSP Cookie 处理 - Cookie 剖析

- 来源：[JSP Cookie 处理](https://www.runoob.com/jsp/jsp-cookies.html)
- 来源章节：[0949-jsp-cookies-study.md](../chapters/0949-jsp-cookies-study.md)
- 分类：后端开发
- 技术：JSP
- 所在小节：Cookie 剖析
- 知识类型：解释
- 原章节序号：0949

## 原文片段

在 JSP 中，设置一个 cookie 需要发送如下的信息头给服务器： HTTP/1.1 200 OK Date: Fri, 04 Feb 2015 21:03:38 GMT Server: Apache/1.3.9 (UNIX) PHP/4.0b3 Set-Cookie: name=runoob; expires=Friday, 04-Feb-17 22:03:38 GMT; path=/; domain=runoob.com Connection: close Content-Type: text/html 正如您所见，Set-Cookie 信息头包含一个键值对，一个 GMT（格林尼治标准）时间，一个路径，一个域名。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `Cookie 剖析` 这一小节和 `JSP Cookie 处理` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
