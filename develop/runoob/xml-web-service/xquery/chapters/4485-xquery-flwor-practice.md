# XQuery：XQuery FLWOR 表达式

- 来源：[XQuery FLWOR 表达式](https://www.runoob.com/xquery/xquery-flwor.html)
- 分类：XML / Web Service
- 技术：XQuery
- 笔记类型：练习笔记
- 章节序号：4485

## 本章内容

## XML 实例文档

我们将在下面的例子中继续使用这个 "books.xml" 文档（与上一节中的 XML 文件相同）。

在您的浏览器中查看 "books.xml" 文件。


## 如果使用 FLWOR 从 "books.xml" 选取节点

请看下面这个路径表达式：

上面这个表达式可选取 bookstore 元素下的 book 元素下所有的 title 元素，并且其中的 price 元素的值必须大于 30。

下面这个 FLWOR 表达式所选取的数据和上面的路径表达式是相同的：

输出结果：

通过 FLWOR，您可以对结果进行排序：

FLWOR 是 "For, Let, Where, Order by, Return" 的只取首字母缩写。

for 语句把 bookstore 元素下的所有 book 元素提取到名为 $x 的变量中。

where 语句选取了 price 元素值大于 30 的 book 元素。

order by 语句定义了排序次序。将根据 title 元素进行排序。

return 语句规定返回什么内容。在此返回的是 title 元素。

上面的 XQuery 表达式的结果：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XQuery FLWOR 表达式` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
