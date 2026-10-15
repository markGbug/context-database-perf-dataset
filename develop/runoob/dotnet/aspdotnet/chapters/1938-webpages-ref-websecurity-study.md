# ASP.NET：ASP.NET Web Pages - WebSecurity 对象

- 来源：[WebPages 安全](https://www.runoob.com/aspnet/webpages-ref-websecurity.html)
- 分类：.NET
- 技术：ASP.NET
- 笔记类型：学习笔记
- 章节序号：1938

## 本章内容

## 描述

WebSecurity 对象提供 ASP.NET Web Pages 应用程序的安全性和认证。

通过 WebSecurity 对象，您可以创建用户帐户，登录和注销用户，重置或者更改密码，以及其他更多与安全性相关的功能。


## WebSecurity 对象参考手册 - 属性


## WebSecurity 对象参考手册 - 方法


## 技术数据


## 初始化 WebSecurity 数据库

如果您想在您的代码中使用 WebSecurity 对象，首先您必须创建或者初始化 WebSecurity 数据库。

在您的 Web 根目录下，创建一个名为 _AppStart.cshtml 的页面（如果已存在，则直接编辑页面）。

将下面的代码复制到文件中：


## _AppStart.cshtml

上面的代码将在每次网站（应用程序）启动时运行。它初始化了 WebSecurity 数据库。

"Users" 是 WebSecurity 数据库（Users.sdf）的名称。

"UserProfile" 是包含用户配置信息的数据库表的名称。

"UserId" 是包含用户 ID（主键）的列的名称。

"Email" 是包含用户名的列的名称。

最后一个参数 true 是一个布尔值，表示如果用户配置表和会员表不存在，则会自动创建表。如果不想自动创建表，应设置参数为 false。


## WebSecurity 数据库

UserProfile 表为每个用户创建保存一条记录，用户 ID（主键）和用户名字（email）：

Membership 表包含会员信息，比如用户是什么时候创建的，该会员是否已认证，会员是什么时候认证的，等等。

具体如下所示（一些列不显示）：

注释：如果您想看到所有的列和内容，请打开数据库，看看里边的每个表。


## 简单的会员配置

在您使用 WebSecurity 对象时，如果您的站点没有配置使用 ASP.NET Web Pages 会员系统 SimpleMembership，可能会报错。

如果托管服务提供商的服务器的配置与您本地服务器的配置不同，也可能会报错。为了解决这个问题，请在网站的 Web.config 文件中添加以下元素：


## 复习重点

- 能说明 `WebPages 安全` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
