# ASP：在自己的 PC 上运行 ASP

- 来源：[ASP 安装](https://www.runoob.com/asp/asp-install.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：学习笔记
- 章节序号：0715

## 本章内容

您可以在自己的 PC 上运行 ASP 。


## 把自己的 Windows PC 作为 Web 服务器

- 如果您安装了 IIS 或 PWS，就可以把自己的 PC 配置为一台 Web 服务器。
- IIS 或 PWS 可以把您的计算机转变为 Web 服务器。
- 微软的 IIS 和 PWS 是免费的 Web 服务器组件。


## IIS - Internet Information Server（Internet 信息服务）

IIS 是一个基于因特网的服务的集合，由微软开发，在微软 Windows 平台上使用。

Windows 2000、XP、Vista 以及 Windows 7 均提供 IIS。Windows NT 也可用 IIS。

IIS 很容易安装，是开发和测试 web 应用程序的理想工具。


## PWS - Personal Web Server

PWS 用于更老的 Windows 系统，比如 Windows 95、98 以及 NT。

PWS 很容易安装，可用于开发和测试包含 ASP 的 Web 应用程序。

我们不推荐使用 PWS，除非是用于培训。它已经过时，并存在安全问题。


## Windows Web 服务器版本

- Windows 7（所有版本）自带 IIS 7.5
- Windows Vista 商业，企业和旗舰版自带 IIS 7
- Windows Vista 高级家庭版自带 IIS 7
- Windows Vista 家庭版不支持 PWS 或 IIS
- Windows XP 专业版自带 IIS 5.1
- Windows XP 家庭版不支持 IIS 或 PWS
- Windows 2000 专业版自带 IIS 5.0
- Windows NT 专业版自带 IIS 3，同时还支持 IIS 4
- Windows NT 工作站支持 PWS 和 IIS 3
- Windows ME 不支持 PWS 或 IIS
- Windows 98 自带 PWS
- Windows 95 支持 PWS


## 如何在 Windows 7 和 Windows Vista 上安装 IIS

请根据以下几个步骤来安装 IIS：

- 从开始菜单打开控制面板
- 双击"程序和功能"
- 点击"打开或关闭 Windows 功能"
- 选择"Internet 信息服务(IIS)"的复选框，然后点击确定

在您安装完成 IIS 之后，请确保安装所有补丁包（运行 Windows 更新）。


## 如何在 Windows XP 和 Windows 2000 上安装 IIS

请根据以下几个步骤来安装 IIS：

- 在开始菜单上，点击设置，并选择控制面板
- 双击"添加/删除程序"
- 点击"添加/删除 Windows 组件"
- 点击"Internet 信息服务(IIS)"
- 点击"详细信息"
- 选择"万维网服务"复选框，点击确定
- 在 Windows 组件中，单击"下一步"安装IIS

在您安装完成 IIS 之后，请确保安装所有补丁包（运行 Windows 更新）。


## 测试您的安装

在您安装完 IIS 或 PWS 之后，按照下面的步骤测试是否安装成功：

- 在您的硬盘中查找名为 Inetpub 的文件夹
- 打开 Inetpub 文件夹，找到名为 wwwroot 的文件夹
- 在 wwwroot下创建一个新文件夹，比如 "MyWeb"
- 使用文本编辑器编写几行 ASP 代码，将这个文件取名为 "test1.asp" 保存在 "MyWeb" 文件夹中
- 确保您的 Web 服务器正在运行，使用下面的方法确认它的运行状态：进入控制面板，然后是管理工具，然后双击"IIS 管理器"图标。
- 打开您的浏览器，在地址栏键入 "http://localhost/MyWeb/test1.asp"，就可以看到您的第一个 ASP 页面了。

注释：在您的开始菜单或者任务栏中查找 IIS (或 PWS) 符号。程序提供了开启和停止 Web 服务器，启用和禁用 ASP，以及其他更多的功能。


## 如何在 Windows 95、Windows 98 和 Windows NT 上安装 PWS

Windows 98：打开您的 Windows CD 上的 Add-ons 文件夹，找到 PWS 文件夹并运行其中的 setup.exe 文件来安装 PWS。

Windows 95 或 Windows NT：从微软的站点下载 "Windows NT 4.0 Option Pack" 来安装 PWS。

根据前面的描述测试您的安装。


## 如何在 Windows Server 2003 上安装 IIS

- 当您启动 Windows Server 2003 后，您会看到服务器管理向导
- 如果向导没有显示，请打开管理工具，然后选择配置您的服务器向导
- 在向导中，点击 Add or Remove a Role，点击下一步
- 选择自定义配置，点击下一步
- 选择应用程序服务器角色，点击下一步
- 选择启用 ASP.NET，点击下一步
- 现在，向导会请求 Server 2003 CD。插入 CD 后继续运行向导直到完成，然后点击完成按钮
- 向导现在应该显示"应用程序服务器角色已安装"
- 点击管理此应用程序服务器打开应用程序服务器管理控制台(MMC)
- 展开 Internet 信息服务(IIS)管理器，然后展开您的服务器，然后是站点文件夹
- 您会看到默认的网站，并且它的状态应该是运行中
- IIS 正在运行中！
- 在 Internet 信息服务(IIS)管理器中点击 Web 服务扩展文件夹
- 这里，您将看到 Active Server Pages 是被禁止的（这是 IIS 6 的默认配置）
- 选中 Active Server Pages，并且点击允许按钮
- 这样 ASP 就被激活了！


## 复习重点

- 能说明 `ASP 安装` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
