# 知识点 44221：MVC：WebForms 事件 - Page.IsPostBack 属性

- 来源：[WebForms 事件](https://www.runoob.com/aspnet/aspnet-events.html)
- 来源章节：[2029-aspnet-events-study.md](../chapters/2029-aspnet-events-study.md)
- 分类：.NET
- 技术：MVC
- 所在小节：Page.IsPostBack 属性
- 知识类型：解释
- 原章节序号：2029

## 原文片段

Page_Load 子例程会在页面每次加载时运行。如果您只想在页面第一次加载时执行 Page_Load 子例程中的代码，那么您可以使用 Page.IsPostBack 属性。如果 Page.IsPostBack 属性设置为 false，则页面第一次被载入，如果设置为 true，则页面被传回到服务器（比如，通过点击表单上的按钮）：

## 学习理解

这是本章正文中的解释型知识点。复习时应先确认关键词，再用自己的话复述它解决的问题。

- 这句话定义了什么？
- 它解释的是原因、规则、场景还是限制？
- 能否用一个小例子验证或说明？

## 复习问题

- `Page.IsPostBack 属性` 这一小节和 `WebForms 事件` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
