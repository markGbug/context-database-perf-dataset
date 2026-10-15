# Web Pages：ASP.NET Web Pages - 文件夹

- 来源：[WebPages 文件夹](https://www.runoob.com/aspnet/webpages-folders.html)
- 分类：.NET
- 技术：Web Pages
- 笔记类型：学习笔记
- 章节序号：2197

## 本章内容

本章介绍有关文件夹和文件夹路径的知识。

在本章中，您将学到：

- 逻辑文件夹结构和物理文件夹结构
- 虚拟名称和物理名称
- Web URL 和 Web 路径


## 逻辑文件夹结构

下面是典型的 ASP.NET 网站文件夹结构：

- "Account" 文件夹包含登录和安全文件
- "App_Data" 文件夹包含数据库和数据文件
- "Images" 文件夹包含图片
- "Scripts" 文件夹包含浏览器脚本
- "Shared" 文件夹包含公共的文件（比如布局和样式文件）


## 物理文件夹结构

在上述网站中的"Images"文件夹在计算机上的物理文件夹结构可能如下：

C:\Documents\MyWebSites\Demo\Images


## 虚拟名称和物理名称

以上面的例子为例：

网站图片的虚拟名称可能是"Images/pic31.jpg"。

对应的物理名称是"C:\Documents\MyWebSites\Demo\Images\pic31.jpg"。


## URL 和路径

URL 是用来访问网站中的文件： http://www.runoob.com/html/html-tutorial.html

URL 对应于服务器上的物理文件：C:\MyWebSites\runoob\html\html-tutorial.html

虚拟路径是物理路径的一种简写表示。如果您使用虚拟路径，当您更改域名或者将您的网页移到其他服务器上时，您可以不用更新路径。

磁盘驱动器的根目录如下书写 C: ，但是网站的根目录是 / （斜线）。

Web 文件夹的虚拟路径通常是与物理文件夹不相同。

在您的代码中，根据您的编码需要决定使用物理路径和和虚拟路径。

ASP.NET 文件夹路径有 3 种工具：~ 运算符、Server.MapPath 方法 和 Href 方法。


## ~ 运算符

使用 ~ 运算符，在编程代码中规定虚拟路径。

如果您使用 ~ 运算符，在您的站点迁移到其他不同的文件夹或者位置时，您可以不用更改您的任何代码：


## Server.MapPath 方法

Server.MapPath 方法将虚拟路径（/index.html）转换成服务器能理解的物理路径（C:\Documents\MyWebSites\Demo\default.html）。

当您需要打开服务器上的数据文件时，您可以使用这个方法（只有提供完整的物理路径才能访问数据文件）：

在本教程的下一章中，您会学到更多关于读取（和写入）服务器上的数据文件的知识。


## Href 方法

Href 方法将代码中的使用的路径转换成浏览器可以理解的路径（浏览器无法理解 ~ 运算符）。

您可以使用 Href 方法创建资源（比如图像文件 和 CSS 文件）的路径。

一般会在 HTML 中的 <a>、<img> 和 <link> 元素中使用此方法:

Href 方法是 WebPage 对象的一种方法。


## 复习重点

- 能说明 `WebPages 文件夹` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
