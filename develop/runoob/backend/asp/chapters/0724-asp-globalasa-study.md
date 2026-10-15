# ASP：ASP Global.asa 文件

- 来源：[ASP Global.asa](https://www.runoob.com/asp/asp-globalasa.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：学习笔记
- 章节序号：0724

## 本章内容

## Global.asa 文件

Global.asa 文件是一个可选的文件，它可包含被 ASP 应用程序中每个页面访问的对象、变量和方法的声明。

所有合法的浏览器脚本（JavaScript、VBScript、JScript、PerlScript 等等）都能在 Global.asa 中使用。

Global.asa 文件只能包含下列内容：

- Application 事件
- Session 事件
- <object> 声明
- TypeLibrary 声明
- #include 指令

注释：Global.asa 文件必须存放在 ASP 应用程序的根目录中，而且每个应用程序只能有一个 Global.asa 文件。


## Global.asa 中的事件

在 Global.asa 中，您可以告诉 application 和 session 对象当 application/session 开始时做什么，当 application/session 结束时做什么。完成这项任务的代码被放置在事件句柄中。Global.asa 文件能包含四种类型的事件：

Session_OnStart - 此事件会在每当新用户请求他（她）在 ASP 应用程序中的第一个页面时发生。

Session_OnEnd - 此事件会在每当用户结束 session 时发生。在规定的时间（默认的时间为 20 分钟）内如果用户没有请求任何页面，用户 session 就会结束。

Application_OnEnd - 此事件会在最后一个用户结束其 session 之后发生。典型的情况是，此事件会在 Web 服务器停止时发生。这个子程序用于在应用程序停止后清除设置，比如删除记录或者向文本文件中写入信息。

一个 Global.asa 文件可能如下所示：

注释：由于我们无法在 Global.asa 文件中使用 ASP 的脚本分隔符 (<% 和 %>) 插入脚本，我们需要把子例程放置在 HTML 的 <script> 元素内部。


## <object> 声明

可通过使用 <object> 标签在 Global.asa 文件中创建带有 session 或者 application 作用域的对象。

注释：<object> 标签应位于 <script> 标签外部！


### 语法

ProgID 或 ClassID 必需被指定。


### 实例

第一个实例通过使用 ProgID 参数创建了一个名为 "MyAd" 的 session 作用域对象：

第二个实例通过使用 ClassID 参数创建了一个名为 "MyConnection" 的 application 作用域对象：

在 Global.asa 文件中声明的对象可被应用程序中的任何脚本使用：


## TypeLibrary 声明

TypeLibrary（类型库）是一个容器，其中装有对应于 COM 对象的 DLL 文件。通过在 Global.asa 文件中包含对 TypeLibrary 的调用，可以访问 COM 对象的常量，同时 ASP 代码也能更好地报告错误。如果您的 Web 应用程序依赖于已在类型库中声明的数据类型的 COM 对象，您可以在 Global.asa 中对类型库进行声明。


### 语法

file 参数或者 uuid 参数，两者缺一不可。


### 错误值

服务器会返回以下的错误消息之一：

注释：METADATA 标签可出现在 Global.asa 文件中的任何位置（在 <script> 标签的内外皆可）。然而，我们还是推荐将 METADATA 标签放置于 Global.asa 文件的顶部。


## 限定

关于可以在 Global.asa 文件中引用的内容的限定：

- 您无法显示 Global.asa 文件中的文本。此文件无法显示信息。
- 您只能在 Application_OnStart 和 Application_OnEnd 子例程中使用 Server 和 Application 对象。在 Session_OnEnd 子例程中，您可以使用 Server、Application 和 Session 对象。在 Session_OnStart 子例程中，您可以使用任何内建的对象。


## 如何使用子例程

Global.asa 常用于初始化变量。

下面的实例演示了如何检测访客首次到达 Web 站点的确切时间。时间存储在名为 "started" 的 Session 对象中，并且 "started" 变量的值可被应用程序中的任何 ASP 页面访问：

Global.asa 也可用于控制页面访问。

下面的实例演示了如何把每个新的访客重定向到另一个页面，在这个例子中会定向到一个名为 "newpage.asp" 的页面：

您可以在 Global.asa 文件中包含函数。

在下面的实例中，当 Web 服务器启动时，Application_OnStart 子例程也会启动。然后，Application_OnStart 子例程会调用另一个名为 "getcustomers" 的子例程。"getcustomers" 子例程会打开一个数据库，然后从 "customers" 表中取回一个记录集。此记录集会赋值给一个数组，在不查询数据库的情况下，任何 ASP 页面都能够访问这个数组：


## Global.asa 实例

在这个实例中，我们将创建一个计算当前访客数量的 Global.asa 文件。

- 当服务器启动时，Application_OnStart 设置 Application 变量 "visitors" 的值为 0。
- 每当有新的访客来访时，Session_OnStart 子例程就会给变量 "visitors" 加 1。
- 每当 Session_OnEnd 子例程被触发时，该子例程就会从变量 "visitors" 减 1。

Global.asa 文件：

在 ASP 文件中，显示当前访客的数量：


## 复习重点

- 能说明 `ASP Global.asa` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
