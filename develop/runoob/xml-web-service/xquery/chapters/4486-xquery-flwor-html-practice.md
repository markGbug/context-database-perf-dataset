# XQuery：XQuery FLWOR + HTML

- 来源：[XQuery FLWOR + HTML](https://www.runoob.com/xquery/xquery-flwor-html.html)
- 分类：XML / Web Service
- 技术：XQuery
- 笔记类型：练习笔记
- 章节序号：4486

## 本章内容

## XML 实例文档

我们将在下面的例子中继续使用这个 "books.xml" 文档（与上一节中的文件相同）。

在您的浏览器中查看 "books.xml" 文件。


## 在一个 HTML 列表中提交结果

请看下面的 XQuery FLWOR 表达式：

上面的表达式会选取 bookstore 元素下的 book 元素下的所有 title 元素，并以字母顺序返回 title 元素。

现在，我们希望使用 HTML 列表列出我们的书店中所有的书目。我们向 FLWOR 表达式添加 <ul> 和 <li> 标签：

以上代码输出结果：

现在我们希望去除 title 元素，而仅仅显示 title 元素内的数据。

结果将是一个 HTML 列表：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XQuery FLWOR + HTML` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
