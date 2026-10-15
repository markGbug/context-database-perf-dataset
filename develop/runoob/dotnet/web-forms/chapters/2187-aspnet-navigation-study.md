# Web Forms：ASP.NET Web Forms - 导航

- 来源：[WebForms 导航](https://www.runoob.com/aspnet/aspnet-navigation.html)
- 分类：.NET
- 技术：Web Forms
- 笔记类型：学习笔记
- 章节序号：2187

## 本章内容

ASP.NET 带有内建的导航控件。


## 网站导航

维护大型网站的菜单是困难而且费时的。

在 ASP.NET 中，菜单可存储在文件中，这样易于维护。文件通常名为 web.sitemap，并且被存放在网站的根目录下。

此外，ASP.NET 有三个新的导航控件：

- Dynamic menus
- TreeViews
- Site Map Path


## Sitemap 文件

在本教程中，使用下面的 sitemap 文件：

创建 sitemap 文件的规则：

- XML 文件必须包含 围绕内容的 <siteMap> 标签
- <siteMap> 标签只能有一个 <siteMapNode> 子节点（ "home" 页面）
- 每个 <siteMapNode> 可以有多个子节点（网页）
- 每个 <siteMapNode> 带有定义页面标题和 URL 的属性

注释：sitemap 文件必须位于站点根目录下，URL 属性必须相对于该根目录。


## 动态菜单

<asp:Menu> 控件可显示标准的站点导航菜单。

代码实例：

上面实例中的 <asp:Menu> 控件是一个供服务器创建导航菜单的占位符。

控件的数据源由 DataSourceId 属性定义。 id="nav1" 把数据源连接到 <asp:SiteMapDataSource> 控件。

<asp:SiteMapDataSource> 控件自动连接默认的 sitemap 文件（web.sitemap）。


## TreeView

<asp:TreeView> 控件可显示多级导航菜单。

这种菜单看上去像一棵带有枝叶的树，可通过 + 或 - 符号来打开或关闭。

代码实例：

上面实例中的 <asp:TreeView> 控件是一个供服务器创建导航菜单的占位符。

控件的数据源由 DataSourceId 属性定义。 id="nav1" 把数据源连接到 <asp:SiteMapDataSource> 控件。

<asp:SiteMapDataSource> 控件自动连接默认的 sitemap 文件（web.sitemap）。


## SiteMapPath

SiteMapPath 控件可显示指向当前页面的指针（导航路径）。该路径显示为指向上级页面的可点击链接。

与 TreeView 和 Menu 控件不同，SiteMapPath 控件不使用 SiteMapDataSource。SiteMapPath 控件默认使用 web.sitemap 文件。

提示：如果 SiteMapPath 没有正确显示，很可能是由于 web.sitemap 文件中存在 URL 错误（打印错误）。

代码实例：

上面实例中的 <asp:SiteMapPath> 控件是一个供服务器创建导航菜单的占位符。


## 复习重点

- 能说明 `WebForms 导航` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
