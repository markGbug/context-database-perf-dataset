# ASP.NET：ASP.NET Web Forms - HTML 表单

- 来源：[WebForms 表单](https://www.runoob.com/aspnet/aspnet-forms.html)
- 分类：.NET
- 技术：ASP.NET
- 笔记类型：练习笔记
- 章节序号：1966

## 本章内容

所有的服务器控件都必须出现在 <form> 标签中，<form> 标签必须包含 runat="server" 属性。


## ASP.NET Web 表单

所有的服务器控件都必须出现在 <form> 标签中，<form> 标签必须包含 runat="server" 属性。runat="server" 属性表明该表单必须在服务器上进行处理。同时也表明了包含在它内部的控件可被服务器脚本访问：

注释：该表单总是被提交到自身页面。如果您指定了一个 action 属性，它会被忽略。如果您省略了 method 属性，它将会默认设置 method="post"。同时，如果您没有指定 name 和 id 属性，它们会由 ASP.NET 自动分配。

注释：一个 .aspx 页面只能包含一个 <form runat="server"> 控件！

如果您在一个包含不带有 name、method、action 或 id 属性的表单的 .aspx 页面中选择查看源代码，您会看到 ASP.NET 添加这些属性到表单上了，如下所示：


## 提交表单

表单通常通过点击按钮来提交。ASP.NET 中的 Button 服务器控件的格式如下：

id 属性为按钮定义了一个唯一的名称，text 属性为按钮分配了一个标签。onClick 事件句柄规定了一个要执行的已命名的子例程。

在下面的例子中，我们在一个 .aspx 文件中声明了一个按钮控件。一次鼠标单击就可以运行一个子例程，可以更改该按钮上的文本。

实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebForms 表单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
