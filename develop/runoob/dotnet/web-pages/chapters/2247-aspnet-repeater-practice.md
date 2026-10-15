# Web Pages：ASP.NET Web Forms - Repeater 控件

- 来源：[WebForms Repeater](https://www.runoob.com/aspnet/aspnet-repeater.html)
- 分类：.NET
- 技术：Web Pages
- 笔记类型：练习笔记
- 章节序号：2247

## 本章内容

Repeater 控件用于显示被绑定在该控件上的项目的重复列表。


## 绑定 DataSet 到 Repeater 控件

Repeater 控件用于显示被绑定在该控件上的项目的重复列表。Repeater 控件可被绑定到数据库表、XML 文件或者其他项目列表。在这里，我们将演示如何绑定 XML 文件到 Repeater 控件。

在我们的实例中，我们将使用下面的 XML 文件（"cdcatalog.xml"）：

查看这个 XML 文件：cdcatalog.xml

首先，导入 "System.Data" 命名空间。我们需要该命名空间与 DataSet 对象一起工作。 把下面这条指令包含在 .aspx 页面的顶部：

接着，为 XML 文件创建一个 DataSet，并在页面第一次加载时把这个 XML 文件载入 DataSet：

然后我们在 .aspx 页面中创建一个 Repeater 控件。<HeaderTemplate> 元素中的内容被首先呈现，并且在输出中仅出现一次，而 <ItemTemplate> 元素中的内容会对应 DataSet 中的每条 "record" 重复出现，最后，<FooterTemplate> 元素中的内容在输出中仅出现一次：

然后我们添加创建 DataSet 的脚本，并且绑定 mycdcatalog DataSet 到 Repeater 控件。然后 使用 HTML 标签来填充 Repeater 控件，并通过 <%#Container.DataItem("fieldname")%> 绑定数据项目到 <ItemTemplate> 区域内的单元格中：


## 实例


## 使用 <AlternatingItemTemplate>

您可以在 <ItemTemplate> 元素后添加 <AlternatingItemTemplate> 元素，用来描述输出中交替行的外观。在下面的实例中，表格每隔一行就会显示为浅灰色的背景：


## 实例


## 使用 <SeparatorTemplate>

<SeparatorTemplate> 元素用于描述每个记录之间的分隔符。在下面的实例中，每个表格行之间插入了一条水平线：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebForms Repeater` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
