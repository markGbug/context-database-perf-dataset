# 知识点 24720：Razor：WebForms ViewState - 维持 ViewState（视图状态）

- 来源：[WebForms ViewState](https://www.runoob.com/aspnet/aspnet-viewstate.html)
- 来源章节：[2111-aspnet-viewstate-study.md](../chapters/2111-aspnet-viewstate-study.md)
- 分类：.NET
- 技术：Razor
- 所在小节：维持 ViewState（视图状态）
- 知识类型：解释
- 原章节序号：2111

## 原文片段

在 ASP .NET 中，当一个表单被提交时，表单会连同表单值一起出现在浏览器窗口中。如何做到的呢？这是因为 ASP .NET 维持了您的 ViewState。ViewState 会在页面被提交到服务器时表明它的状态。这个状态是通过在带有 <form runat="server"> 控件的每个页面上放置一个隐藏域定义的。源代码如下所示：

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `维持 ViewState（视图状态）` 这一小节和 `WebForms ViewState` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
