# Web Forms：ASP.NET Web Pages - WebMail 对象

- 来源：[WebPages 邮局](https://www.runoob.com/aspnet/webpages-ref-webmail.html)
- 分类：.NET
- 技术：Web Forms
- 笔记类型：学习笔记
- 章节序号：2148

## 本章内容

通过 WebMail 对象，您可以很容易地从网页上发送电子邮件。


## 描述

WebMail 对象为 ASP.NET Web Pages 提供了使用 SMTP（Simple Mail Transfer Protocol 简单邮件传输协议）发送邮件的功能。


## 实例

请查看 WebPages Email 章节中的实例。


## WebMail 对象参考手册 - 属性


## WebMail 对象参考手册 - 方法

Send() 方法有以下参数：

Send() 方法有以下可选参数：


## 技术数据


## 初始化 WebMail 帮助器

要使用 WebMail 帮助器，您必须能访问 SMTP 服务器。SMTP 是电子邮件的"输出"部分。如果您使用的是虚拟主机，您可能已经知道 SMTP 服务器的名称。如果您使用的是公司网络工作，您公司的 IT 部门会给您一个名称。如果您是在家工作，你也许可以使用普通的电子邮件服务提供商。

为了发送一封电子邮件，您将需要：

- SMTP 服务器的名称
- 端口号（通常是 25 ）
- 电子邮件的用户名
- 电子邮件的密码

在您的 Web 根目录下，创建一个名为 _AppStart.cshtml 的页面（如果已存在，则直接编辑页面）。

将下面的代码复制到文件中：


## _AppStart.cshtml

上面的代码将在每次网站（应用程序）启动时运行。它对 WebMail 对象赋了初始值。

请替换：

将 smtp.example.com 替换成您要用来发送电子邮件的 SMTP 服务器的名称。

将 25 替换成服务器用来发送 SMTP 事务（电子邮件）的端口号。

如果服务器使用 SSL（Secure Socket Layer 安全套接层）加密，请将 false 替换成 true。

将 support@example.com 替换成用来发送电子邮件的 SMTP 电子邮件账户的名称。

将 password 替换成 SMTP 电子邮件账户的密码。

将 john@example 替换成显示在发件地址栏中的电子邮件。


## 复习重点

- 能说明 `WebPages 邮局` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
