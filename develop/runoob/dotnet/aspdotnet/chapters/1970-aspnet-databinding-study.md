# ASP.NET：ASP.NET Web Forms - 数据绑定

- 来源：[WebForms 数据绑定](https://www.runoob.com/aspnet/aspnet-databinding.html)
- 分类：.NET
- 技术：ASP.NET
- 笔记类型：学习笔记
- 章节序号：1970

## 本章内容

我们可以使用数据绑定（Data Binding）来完成带可选项的列表，这些可选项来自某个导入的数据源，比如数据库、XML 文件或者脚本。


## 数据绑定

下面的控件是支持数据绑定的列表控件：

- asp:RadioButtonList
- asp:CheckBoxList
- asp:DropDownList
- asp:Listbox

以上每个控件的可选项通常是在一个或者多个 asp:ListItem 控件中定义，如下：

然而，我们可以使用某种独立的数据源进行数据绑定，比如数据库、XML 文件或者脚本，通过数据绑定来填充列表的可选项。

通过使用导入的数据源，数据从 HTML 中分离出来，并且对可选项的修改都是在独立的数据源中完成的。

在下面的三个章节中，我们将描述如何从脚本化的数据源中绑定数据。


## 复习重点

- 能说明 `WebForms 数据绑定` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
