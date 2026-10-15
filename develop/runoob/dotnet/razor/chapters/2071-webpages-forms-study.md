# Razor：ASP.NET Web Pages - HTML 表单

- 来源：[WebPages 表单](https://www.runoob.com/aspnet/webpages-forms.html)
- 分类：.NET
- 技术：Razor
- 笔记类型：学习笔记
- 章节序号：2071

## 本章内容

表单是 HTML 文档中放置输入控件（文本框、复选框、单选按钮、下拉列表）的部分。


## 创建一个 HTML 输入页面


## Razor 实例


## Razor 实例 - 显示图像

假设在您的图像文件夹中有 3 张图像，您想根据用户的选择动态地显示图像。

这可以通过一段简单的 Razor 代码来实现。

如果在您的网站的图像文件夹中有一个名为 "Photo1.jpg" 的图像，您可以使用 HTML 的 <img> 元素来显示图像，如下所示：

下面的例子演示了如何显示用户从下列列表中选择的图像：


## Razor 实例


## 实例解释

服务器创建了一个叫 imagePath 的变量。

HTML 页面有一个名为 Choice 的下拉列表（<select> 元素）。它允许用户根据自己的意愿选择一个名称（如 Photo 1），当页面被提交到 Web 服务器时，则传递了一个文件名（如 Photo1.jpg）。

Razor 代码通过 Request["Choice"] 读取 Choice 的值。如果通过代码构建的图像路径（images/Photo1.jpg）有效，就把图像路径赋值给变量 imagePath。

在 HTML 页面中，<img> 元素用来显示图像。当页面显示时，src 属性用来设置 imagePath 变量的值。

<img> 元素是在一个 if 块中，这是为了防止显示没有名称的图像，比如页面第一次被加载显示的时候。


## 复习重点

- 能说明 `WebPages 表单` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
