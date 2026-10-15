# 知识点 22306：Java：Java Override/Overload - 重写(Override)

- 来源：[Java Override/Overload](https://www.runoob.com/java/java-override-overload.html)
- 来源章节：[0904-java-override-overload-study.md](../chapters/0904-java-override-overload-study.md)
- 分类：后端开发
- 技术：Java
- 所在小节：重写(Override)
- 知识类型：解释
- 原章节序号：0904

## 原文片段

重写方法不能抛出新的检查异常或者比被重写方法申明更加宽泛的异常。例如： 父类的一个方法申明了一个检查异常 IOException，但是在重写这个方法的时候不能抛出 Exception 异常，因为 Exception 是 IOException 的父类，抛出 IOException 异常或者 IOException 的子类异常。

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `重写(Override)` 这一小节和 `Java Override/Overload` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
