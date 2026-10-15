# Web Pages：ASP.NET Web Pages - WebMail 帮助器

- 来源：[WebPages Email](https://www.runoob.com/aspnet/webpages-email.html)
- 分类：.NET
- 技术：Web Pages
- 笔记类型：练习笔记
- 章节序号：2205

## 本章内容

WebMail 帮助器 - 众多有用的 ASP.NET Web 帮助器之一。


## WebMail 帮助器

WebMail 帮助器让发送邮件变得更简单，它按照 SMTP（Simple Mail Transfer Protocol 简单邮件传输协议）从 Web 应用程序发送邮件。


## 前提：电子邮件支持

为了演示如何使用电子邮件，我们将创建一个输入页面，让用户提交一个页面到另一个页面，并发送一封关于支持问题的邮件。


## 第一：编辑您的 AppStart 页面

如果在本教程中您已经创建了 Demo 应用程序，那么您已经有一个名为 _AppStart.cshtml 的页面，内容如下：


## _AppStart.cshtml

要启动 WebMail 帮助器，向您的 AppStart 页面中增加如下所示的 WebMail 属性：


## _AppStart.cshtml

属性解释：

SmtpServer: 用于发送电子邮件的 SMTP 服务器的名称。

SmtpPort: 服务器用来发送 SMTP 事务（电子邮件）的端口。

EnableSsl: 如果服务器使用 SSL（Secure Socket Layer 安全套接层）加密，则值为 true。

UserName: 用于发送电子邮件的 SMTP 电子邮件账户的名称。

Password: SMTP 电子邮件账户的密码。

From: 在发件地址栏显示的电子邮件（通常与 UserName 相同）。


## 第二：创建一个电子邮件输入页面

接着创建一个输入页面，并将它命名为 Email_Input：


## Email_Input.cshtml

输入页面的目的是手机信息，然后提交数据到可以将信息作为电子邮件发送的一个新的页面。


## 第三：创建一个电子邮件发送页面

接着创建一个用来发送电子邮件的页面，并将它命名为 Email_Send：


## Email_Send.cshtml

想了解更多关于 ASP.NET Web Pages 应用程序发送电子邮件的信息，请查阅：WebMail 对象参考手册。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebPages Email` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
