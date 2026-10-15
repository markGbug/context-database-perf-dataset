# 知识点 47614：Ruby：Ruby Socket 编程 - 什么是 Sockets

- 来源：[Ruby Socket 编程](https://www.runoob.com/ruby/ruby-socket-programming.html)
- 来源章节：[3748-ruby-socket-programming-practice.md](../chapters/3748-ruby-socket-programming-practice.md)
- 分类：编程语言
- 技术：Ruby
- 所在小节：什么是 Sockets
- 知识类型：解释
- 原章节序号：3748

## 原文片段

应用层通过传输层进行数据通信时，TCP和UDP会遇到同时为多个应用程序进程提供并发服务的问题。多个TCP连接或多个应用程序进程可能需要 通过同一个TCP协议端口传输数据。为了区别不同的应用程序进程和连接，许多计算机操作系统为应用程序与TCP／IP协议交互提供了称为套接字 (Socket)的接口，区分不同应用程序进程间的网络通信和连接。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `什么是 Sockets` 这一小节和 `Ruby Socket 编程` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
