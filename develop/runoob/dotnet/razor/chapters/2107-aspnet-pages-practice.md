# Razor：ASP.NET Web Forms - HTML 页面

- 来源：[WebForms 页面](https://www.runoob.com/aspnet/aspnet-pages.html)
- 分类：.NET
- 技术：Razor
- 笔记类型：练习笔记
- 章节序号：2107

## 本章内容

简单的 ASP.NET 页面看上去就像普通的 HTML 页面。


## Hello RUNOOB.COM

在开始学习 ASP.NET 之前，我们先来构建一个简单的 HTML 页面，该页面将在浏览器中显示 "Hello RUNOOB.COM"：


## Hello RUNOOB.COM!


## 用 HTML 编写的 Hello RUNOOB.COM

下面的代码将以 HTML 页面的形式显示实例：

如果您想亲自尝试一下，请保存上面的代码到一个名为 "firstpage.htm" 的文件中，并创建一个到该文件的链接：firstpage.htm。


## 用 ASP.NET 编写的 Hello RUNOOB.COM

转换 HTML 页面为 ASP.NET 页面最简单的方法是，直接复制一个 HTML 文件，并把新文件的扩展名改成 .aspx 。

下面的代码将以 ASP.NET 页面的形式显示实例：

如果您想亲自尝试一下，请保存上面的代码到一个名为 "firstpage.aspx" 的文件中，并创建一个到该文件的链接：firstpage.aspx。


## 它是如何工作的？

从根本上讲，ASP.NET 页面与 HTML 是完全相同的。

HTML 页面的扩展名是 .htm。如果浏览器向服务器请求一个 HTML 页面，服务器可以不进行任何修改，就直接发送页面给浏览器。

ASP.NET 页面的扩展名是 .aspx。如果浏览器向服务器请求个 ASP.NET 页面，服务器在将结果发回给浏览器之前，需要先处理页面中的可执行代码。

上面的 ASP.NET 页面不包含任何可执行的代码，所以没有执行任何东西。在下面的实例中，我们将添加一些可执行的代码到页面中，以便演示静态 HTML 页面和动态 ASP 页面的不同之处。


## 经典 ASP

Active Server Pages (ASP) 已经流行很多年了。通过 ASP，可以在 HTML 页面中放置可执行代码。

之前的 ASP 版本（在 ASP.NET 之前）通常被称为经典 ASP。

ASP.NET 不完全兼容经典 ASP，但是只需要经过少量的修改，大部分经典 ASP 页面就可以作为 ASP.NET 页面良好地运行。

如果您想学习更多关于经典 ASP 的知识，请访问我们的 ASP 教程。


## 用经典 ASP 编写的动态页面

为了演示 ASP 是如何显示包含动态内容的页面，我们将向上面的实例中添加一些可执行的代码（红色字体标识）：

<% --%> 标签内的代码是在服务器上执行的。

Response.Write 是用来向 HTML 输出流中写东西的 ASP 代码。

Now() 是一个返回服务器当前日期和时间的函数。

如果您想亲自尝试一下，请保存上面的代码到一个名为 "dynpage.asp" 的文件中，并创建一个到该文件的链接：dynpage.asp。


## 用 ASP .NET 编写的动态页面

下面的代码将以 ASP.NET 页面的形式显示实例：

如果您想亲自尝试一下，请保存上面的代码到一个名为 "dynpage.aspx" 的文件中，并创建一个到该文件的链接：dynpage.aspx。


## ASP.NET 对比经典 ASP

上面的实例无法演示 ASP.NET 与经典 ASP 之间任何的不同之处。

正如最后的两个实例中，您看不出 ASP 页面和 ASP.NET 页面两者之间的不同之处。

在下一章中，您将看到服务器控件是如何让 ASP.NET 比经典 ASP 更强大的。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebForms 页面` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
