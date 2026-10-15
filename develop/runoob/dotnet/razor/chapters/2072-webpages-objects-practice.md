# Razor：ASP.NET Web Pages - 对象

- 来源：[WebPages 对象](https://www.runoob.com/aspnet/webpages-objects.html)
- 分类：.NET
- 技术：Razor
- 笔记类型：练习笔记
- 章节序号：2072

## 本章内容

Web Pages 经常是跟对象有关的。


## Page 对象

您已经看到了一些在使用的 Page 对象方法：

在前面的章节中，您已经看到了两个 Page 对象属性（isPost 和 Request）：


## 某些 Page 对象方法


## 某些 Page 对象属性


## Page 对象的 Page 属性

Page 对象的 Page 属性，提供了对页面和布局页之间共享的数据的类似属性访问。

您可以对 Page 属性使用（添加）您自己的属性：

- Page.Title
- Page.Version
- Page.anythingyoulike

页面属性是非常有用的。例如，在内容文件中设置页面标题，并在布局文件中使用：


## Home.cshtml


## Layout.cshtml


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebPages 对象` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
