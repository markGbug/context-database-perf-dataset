# ASP.NET：ASP.NET Web Forms - 维持 ViewState

- 来源：[WebForms ViewState](https://www.runoob.com/aspnet/aspnet-viewstate.html)
- 分类：.NET
- 技术：ASP.NET
- 笔记类型：练习笔记
- 章节序号：1967

## 本章内容

通过在您的 Web Form 中维持对象的 ViewState（视图状态），您可以省去大量的编码工作。


## 维持 ViewState（视图状态）

在经典 ASP 中，当一个表单被提交时，所有的表单值都会被清空。假设您提交了一个带有大量信息的表单，而服务器返回了一个错误。您不得不回到表单改正信息。您点击返回按钮，然后发生了什么......所有表单值都被清空了，您不得不重新开始所有的一切！站点没有维持您的 ViewState。

在 ASP .NET 中，当一个表单被提交时，表单会连同表单值一起出现在浏览器窗口中。如何做到的呢？这是因为 ASP .NET 维持了您的 ViewState。 ViewState 会在页面被提交到服务器时表明它的状态。这个状态是通过在带有 <form runat="server"> 控件的每个页面上放置一个隐藏域定义的。源代码如下所示：

维持 ViewState 是 ASP.NET Web Forms 的默认设置。如果您想不维持 ViewState，请在 .aspx 页面顶部包含指令 <%@ Page EnableViewState="false" %> ，或者向任意控件添加属性 EnableViewState="false" 。

请看下面的 .aspx 文件。它演示了"老"的运行方式。当您点击提交按钮，表单值将会消失：


## 实例

下面是新的 ASP .NET 方式。当您点击提交按钮，表单值不会消失：


## 实例

点击实例的右边框架中的查看源代码，您将看到 ASP .NET 已经在表单中添加了一个隐藏域来维持 ViewState。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebForms ViewState` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
