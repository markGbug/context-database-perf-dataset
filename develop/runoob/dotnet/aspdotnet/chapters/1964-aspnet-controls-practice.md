# ASP.NET：ASP.NET Web Forms - 服务器控件

- 来源：[WebForms 控件](https://www.runoob.com/aspnet/aspnet-controls.html)
- 分类：.NET
- 技术：ASP.NET
- 笔记类型：练习笔记
- 章节序号：1964

## 本章内容

服务器控件是服务器可理解的标签。


## 经典 ASP 的局限性

下面列出的代码是从上一章中复制的：

上面的代码反映出经典 ASP 的局限性：代码块必须放置在您想要输出显示的位置。

通过经典 ASP，想要把可执行代码从 HTML 页面中分离出来是不可能的。这让页面变得难以阅读，也难以维护。


## ASP.NET - 服务器控件

ASP.NET 通过服务器控件，已经解决了上述的"意大利面条式代码"问题。

服务器控件是服务器可理解的标签。

有三种类型的服务器控件：

- HTML 服务器控件 - 创建的 HTML 标签
- Web 服务器控件 - 新的 ASP.NET 标签
- Validation 服务器控件 - 用于输入验证


## ASP.NET - HTML 服务器控件

HTML 服务器控件是服务器可理解的 HTML 标签。

ASP.NET 文件中的 HTML 元素，默认是作为文本进行处理的。要想让这些元素可编程，需向 HTML 元素中添加 runat="server" 属性。这个属性表示，该元素将被作为服务器控件进行处理。同时需要添加 id 属性来标识服务器控件。id 引用可用于操作运行时的服务器控件。

注释：所有 HTML 服务器控件必须位于带有 runat="server" 属性的 <form> 标签内。runat="server" 属性表明了该表单必须在服务器上进行处理。同时也表明了包含在它内部的控件可被服务器脚本访问。

在下面的实例中，我们在 .aspx 文件中声明了一个 HtmlAnchor 服务器控件。然后我们在一个事件句柄（事件句柄是一种针对给定事件执行代码的子例程）中操作 HtmlAnchor 控件的 HRef 属性。Page_Load 事件是 ASP.NET 可理解的多种事件中的一种：

可执行代码本身已经被移到 HTML 之外了。


## ASP.NET - Web 服务器控件

Web 服务器控件是服务器可理解的特殊 ASP.NET 标签。

就像 HTML 服务器控件，Web 服务器控件也是在服务器上创建的，它们同样需要 runat="server" 属性才能生效。然而，Web 服务器控件没有必要映射任何已存在的 HTML 元素，它们可以表示更复杂的元素。

创建 Web 服务器控件的语法是：

在下面的实例中，我们在 .aspx 文件中声明了一个 Button 服务器控件。然后我们为 Click 事件创建一个事件句柄，用来改变按钮上的文本：


## ASP.NET - Validation 服务器控件

Validation 服务器控件是用来验证用户输入的。如果用户输入没有通过验证，将显示一条错误消息给用户。

每种 validation 控件执行一种指定类型的验证（比如验证某个指定的值或者某个范围的值）。

在默认情况下，当 Button、ImageButton、LinkButton 控件被点击时，会执行页面验证。您可以设置 CausesValidation 为 false ，来阻止按钮控件被点击时进行验证。

创建 Validation 服务器控件的语法是：

在下面的实例中，我们在 .aspx 文件中声明了一个 TextBox 控件、一个 Button 控件、一个 RangeValidator 控件。如果验证失败，文本 "The value must be from 1 to 100!" 将会显示在 RangeValidator 控件中：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebForms 控件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
