# 知识点 80327：Servlet：Servlet 生命周期 - init() 方法

- 来源：[Servlet 生命周期](https://www.runoob.com/servlet/servlet-life-cycle.html)
- 来源章节：[1173-servlet-life-cycle-practice.md](../chapters/1173-servlet-life-cycle-practice.md)
- 分类：后端开发
- 技术：Servlet
- 所在小节：init() 方法
- 知识类型：解释
- 原章节序号：1173

## 原文片段

当用户调用一个 Servlet 时，就会创建一个 Servlet 实例，每一个用户请求都会产生一个新的线程，适当的时候移交给 doGet 或 doPost 方法。init() 方法简单地创建或加载一些数据，这些数据将被用于 Servlet 的整个生命周期。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `init() 方法` 这一小节和 `Servlet 生命周期` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
