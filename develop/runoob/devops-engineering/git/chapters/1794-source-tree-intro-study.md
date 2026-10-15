# Git：Sourcetree 使用教程

- 来源：[Sourcetree](https://www.runoob.com/git/source-tree-intro.html)
- 分类：DevOps / 工程化
- 技术：Git
- 笔记类型：学习笔记
- 章节序号：1794

## 本章内容

Git 有很多图形界面工具 ( GUI )，比如 SourceTree、Github Desktop、TortoiseGit 等。

SourceTree 是一个 Git 客户端管理工具，适用于 Windows 和 Mac 系统。

SourceTree 简化了开发者与代码仓库之间的 Git 操作方式，我们可以通过界面菜单很方便的处理 Git 操作，而不需要通过命令。

通过 SourceTree，我们可以管理所有的 Git 库，无论是远程还是本地的。SourceTree 支持 Bitbucket、GitHub 以及 Gitlab 等远程仓库。


## Sourcetree 安装

我们可以在 Sourcetree 官网 https://www.sourcetreeapp.com/ 直接点击下载按钮来下载：

其他版本可以查看：https://www.sourcetreeapp.com/download-archives

下载完成后，解压 ZIP 文件，双击应用程序文件（Windows 为 EXE 或 Mac 为 DMG）进行安装。

安装过程中，我们只需要同意 Atlassian 客户协议并点击 Continue 即可。

创建 Bitbucket 账户可跳过初始设置，加载 SSH 密钥，如果有会默认加载进来，也可以后面再设置。

按照提示操作，直到您完成设置。如果您还没有准备好克隆存储库，请单击 Skip Setup。


## 连接 Github 账户

如果你还没有 Github 账户需要创建一个，可以参考 Git 远程仓库(Github)。

接下来我们将介绍使用 Sourcetree 管理我们的 Github 账户。

我们可以将多个帐户添加到 Sourcetree。

单击右上角的按钮并选择帐户。

接下来我们通过添加账户按钮添加 Github 账户。

Github 账户添加完成后，就可以直接克隆我们自己的账户：

也可以克隆其他远程仓库：

克隆完成后，我们就可以进行提交、拉取、合并等操作：


## 创建本地仓库

单击新建，然后选择创建本地仓库。

输入您的目标路径和存储库名称，然后点击创建。

创建完成后就会显示在本地的列表中：

如果我们本地已经存在一个仓库，可以直接添加它。

点击新建，然后 点击添加已经存在的本地仓库：


## 复习重点

- 能说明 `Sourcetree` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
