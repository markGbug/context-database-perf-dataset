# MVC：ASP.NET MVC - HTML 帮助器

- 来源：[MVC HTML 帮助器](https://www.runoob.com/aspnet/mvc-htmlhelpers.html)
- 分类：.NET
- 技术：MVC
- 笔记类型：学习笔记
- 章节序号：2023

## 本章内容

HTML 帮助器用于修改 HTML 输出。


## HTML 帮助器

通过 MVC，HTML 帮助器类似于传统的 ASP.NET Web Form 控件。

就像 ASP.NET 中的 Web Form 控件，HTML 帮助器用于修改 HTML。但是 HTML 帮助器是更轻量级的。与 Web Form 控件不同，HTML 帮助器没有事件模型和视图状态。

在大多数情况下，HTML 帮助器仅仅是一个返回字符串的方法。

通过 MVC，您可以创建您自己的帮助器，或者直接使用内建的 HTML 帮助器。


## 标准的 HTML 帮助器

MVC 包含了大多数常用的 HTML 元素类型的标准帮助器，比如 HTML 链接和 HTML 表单元素。


## HTML 链接

呈现 HTML 链接的最简单的方法是使用 HTML.ActionLink() 帮助器。

通过 MVC，Html.ActionLink() 不连接到视图。它创建一个连接到控制器操作。

Razor 语法：

ASP 语法：

第一个参数是链接文本，第二个参数是控制器操作的名称。

上面的 Html.ActionLink() 帮助器，输出以下的 HTML：

Html.ActionLink() 帮助器的一些属性：

注释：您可以向控制器操作传递值。例如，您可以向数据库 Edit 操作传递数据库记录的 id：

Razor 语法 C#：

Razor 语法 VB：

上面的 Html.ActionLink() 帮助器，输出以下的 HTML：


## HTML 表单元素

以下 HTML 帮助器可用于呈现（修改和输出）HTML 表单元素：

- BeginForm()
- EndForm()
- TextArea()
- TextBox()
- CheckBox()
- RadioButton()
- ListBox()
- DropDownList()
- Hidden()
- Password()

ASP.NET 语法 C#：


## 复习重点

- 能说明 `MVC HTML 帮助器` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
