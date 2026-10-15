# MVC：ASP.NET MVC - 样式和布局

- 来源：[MVC 布局](https://www.runoob.com/aspnet/mvc-layout.html)
- 分类：.NET
- 技术：MVC
- 笔记类型：练习笔记
- 章节序号：2017

## 本章内容

为了学习 ASP.NET MVC，我们将构建一个 Internet 应用程序。

第 3 部分：添加样式和统一的外观（布局）。


## 添加布局

文件 _Layout.cshtml 表示应用程序中每个页面的布局。它位于 Views 文件夹中的 Shared 文件夹。

打开文件 _Layout.cshtml，把内容替换成：


## HTML 帮助器

在上面的代码中，HTML 帮助器用于修改 HTML 输出：

@Url.Content() - URL 内容将在此处插入。

@Html.ActionLink() - HTML 链接将在此处插入。

在本教程后面的章节中，您将学到更多关于 HTML 帮助器的知识。


## Razor 语法

在上面的代码中，红色标记的代码是使用 Razor 标记的 C#。

@ViewBag.Title - 页面标题将在此处插入。

@RenderBody() - 页面内容将在此处呈现。

您可以在我们的 Razor 教程中学习关于 C# 和 VB（Visual Basic）的 Razor 标记的知识。


## 添加样式

应用程序的样式表是 Site.css，位于 Content 文件夹中。

打开文件 Site.css，把内容替换成：


## _ViewStart 文件

Shared 文件夹（位于 Views 文件夹内）中的 _ViewStart 文件包含如下内容：

这段代码被自动添加到由应用程序显示的所有视图。

如果您删除了这个文件，则必须向所有视图中添加这行代码。

在本教程后面的章节中，您将学到更多关于视图的知识。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `MVC 布局` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
