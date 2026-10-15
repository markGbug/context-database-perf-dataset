# ASP：ASP Application 对象

- 来源：[ASP Application](https://www.runoob.com/asp/asp-applications.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：练习笔记
- 章节序号：0722

## 本章内容

在一起协同工作以完成某项任务的一组 ASP 文件称为一个应用程序。


## Application 对象

Web 上的一个应用程序可以是一组 ASP 文件。这些 ASP 文件一起协同工作来完成某项任务。ASP 中的 Application 对象用于把这些文件捆绑在一起。

Application 对象用于存储和访问来自任何页面的变量，类似于 Session 对象。不同之处在于，所有的用户分享一个 Application 对象，而 Session 对象和用户的关系是一一对应的。

Application 对象存有会被应用程序中的许多页面使用的信息（比如数据库连接信息）。可以从任何的页面访问这些信息。同时您也可以在一个地方改变这些信息，随后这些改变会自动反映在所有的页面上。


## 存储和取回 Application 变量

Application 变量可被应用程序中的任何页面访问和改变。

您可以在 "Global.asa" 中创建 Application 变量，如下所示：

在上面的实例中，我们创建了两个 Application 变量："vartime" 和 "users"。

您可以访问 Application 变量的值，如下所示：


## 遍历 Contents 集合

Contents 集合包含着所有的 application 变量。您可以通过遍历 Contents 集合，来查看其中存储的变量：

如果您不知道 Contents 集合中的项目数量，您可以使用 Count 属性：


## 遍历 StaticObjects 集合

您可以通过遍历 StaticObjects 集合，来查看存储在 Application 对象中的所有对象的值：


## 锁定和解锁

您可以使用 "Lock" 方法来锁定应用程序。当应用程序锁定后，用户们就无法改变 Application 变量了（除了正在访问 Application 变量的用户）。您还可以使用 "Unlock" 方法来解锁应用程序。这个方法会移除对 Application 变量的锁定：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ASP Application` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
