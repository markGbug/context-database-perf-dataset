# ASP.NET：ASP.NET Web Forms - TextBox 控件

- 来源：[WebForms TextBox](https://www.runoob.com/aspnet/aspnet-textbox.html)
- 分类：.NET
- 技术：ASP.NET
- 笔记类型：学习笔记
- 章节序号：1968

## 本章内容

TextBox 控件用于创建用户可输入文本的文本框。


## TextBox 控件

TextBox 控件用于创建用户可输入文本的文本框。

TextBox 控件的特性和属性列在我们的 WebForms 控件参考手册页面。

下面的实例演示了您可能会用到的 TextBox 控件的一些属性：


## 实例


## 添加脚本

当表单被提交时，TextBox 控件的内容和设置可能会被服务器脚本修改。表单可通过点击一个按钮或当用户修改 TextBox 控件的值的时候进行提交。

在下面的实例中，我们在 .aspx 文件中声明了一个 TextBox 控件、一个 Button 控件和一个 Label 控件。当提交按钮被触发时，submit 子例程将被执行。submit 子例程将写入一行文本到 Label 控件中：


## 实例

在下面的实例中，我们在 .aspx 文件中声明了一个 TextBox 控件和一个 Label 控件。当您修改了 TextBox 中的值，并且在 TextBox 外部点击（或者按下了 Tab 键）时，change 子例程将会被执行。change 子例程将写入一行文本到 Label 控件中：


## 实例


## 复习重点

- 能说明 `WebForms TextBox` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
