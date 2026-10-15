# ASP：ASP Session 对象

- 来源：[ASP Session](https://www.runoob.com/asp/asp-sessions.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：概念卡
- 章节序号：0721

## 本章内容

Session 对象用于存储关于用户会话（session）的信息，或者更改用户会话（session）的设置。


## Session 对象

当您在计算机上操作某个应用程序时，您打开它，做些更改，然后关闭它。这很像一次对话（Session）。计算机知道您是谁。它清楚您在何时打开和关闭应用程序。然而，在因特网上问题出现了：由于 HTTP 地址无法保持状态，Web 服务器并不知道您是谁以及您做了什么。

ASP 通过为每个用户创建一个唯一的 cookie 来解决这个问题。cookie 被传送至用户的计算机上，它含有可识别用户的信息。这种接口被称作 Session 对象。

Session 对象用于存储关于用户会话（session）的信息，或者更改用户会话（session）的设置。

存储于 Session 对象中的变量存储单一用户的信息，并且对于应用程序中的所有页面都是可用的。存储于 session 变量中的公共信息通常是 name、id 和参数。服务器会为每个新的用户创建一个新的 Session，并在 session 失效时撤销掉这个 Session 对象。


## Session 何时开始？

Session 开始于：

- 某个新用户请求了一个 ASP 文件，并且 Global.asa 文件引用了 Session_OnStart 子程序
- 某个值存储在 Session 变量中
- 某个用户请求了一个 ASP 文件，并且 Global.asa 使用 <object> 标签通过 session 的 scope 来实例化某个对象


## Session 何时结束？

如果用户没有在规定的时间内在应用程序中请求或者刷新页面，session 就会结束。默认值为 20 分钟。

如果您想要将超时的时间间隔设置为比默认值更短或更长，可以使用 Timeout 属性。

下面的实例设置了一个 5 分钟的超时时间间隔：

要立即结束 session，请使用 Abandon 方法：

注释：使用 session 时主要的问题是它们该在何时结束。我们不会知道用户最近的请求是否是最后的请求。因此我们不清楚该让 session "存活"多久。为某个空闲的 session 等待太久会耗尽服务器的资源。然而如果 session 被过早地删除，用户就不得不一遍又一遍地重新开始，这是因为服务器已经删除了所有的信息。寻找合适的超时间隔时间是很困难的！

提示：在 session 变量中仅存储少量的数据！


## 存储和取回 Session 变量

Session 对象最大的优点是可在其中存储变量，以供后续的网页读取，其应用范围是很广的。

下面的实例把 "Donald Duck" 赋值给名为 username 的 Session 变量，并把 "50" 赋值给名为 age 的 Session 变量：

当值被存储在 session 变量中，它就能被 ASP 应用程序中的任何页面使用：

上面这行代码返回的结果是: "Welcome Donald Duck"。

您也可以在 Session 对象中存储用户参数，然后通过访问这些参数来决定向用户返回什么页面。

下面的实例规定，假如用户使用低显示器分辨率，则返回纯文本版本的页面：


## 移除 Session 变量

Contents 集合包含所有的 session 变量。

可通过 Remove 方法来移除 session 变量。

在下面的实例中，如果 session 变量 "age" 的值小于 18，则移除 session 变量 "sale"：

如需移除 session 中的所有变量，请使用 RemoveAll 方法：


## 遍历 Contents 集合

Contents 集合包含所有的 session 变量。您可以通过遍历 Contents 集合，来查看其中存储的变量：

结果：

如果您不知道 Contents 集合中的项目数量，您可以使用 Count 属性：

结果：


## 遍历 StaticObjects 集合

您可以通过遍历 StaticObjects 集合，来查看存储在 Session 对象中的所有对象的值：


## 记忆卡片

- 一句话定义：`ASP Session` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
