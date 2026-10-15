# Web Pages：ASP.NET Web Forms - XML 文件

- 来源：[WebForms XML 文件](https://www.runoob.com/aspnet/aspnet-xml.html)
- 分类：.NET
- 技术：Web Pages
- 笔记类型：练习笔记
- 章节序号：2246

## 本章内容

我们可以绑定 XML 文件到列表控件。


## 一个 XML 文件

这里有一个名为 "countries.xml" 的 XML 文件：

查看这个 XML 文件：countries.xml


## 绑定 DataSet 到 List 控件

首先，导入 "System.Data" 命名空间。我们需要该命名空间与 DataSet 对象一起工作。把下面这条指令包含在 .aspx 页面的顶部：

接着，为 XML 文件创建一个 DataSet，并在页面第一次加载时把这个 XML 文件载入 DataSet：

为了绑定数据到 RadioButtonList 控件，首先要在 .aspx 页面中创建一个 RadioButtonList 控件（不带任何 asp:ListItem 元素）：

然后添加创建 XML DataSet 的脚本，并且绑定 XML DataSet 中的值到 RadioButtonList 控件：

然后我们添加一个子例程，当用户点击 RadioButtonList 控件中的某个项目时，该子例程会被执行。当某个单选按钮被点击时，label 中会出现一行文本：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebForms XML 文件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
