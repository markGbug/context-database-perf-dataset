# Razor：ASP.NET Web Forms - DataList 控件

- 来源：[WebForms DataList](https://www.runoob.com/aspnet/aspnet-datalist.html)
- 分类：.NET
- 技术：Razor
- 笔记类型：练习笔记
- 章节序号：2120

## 本章内容

DataList 控件，类似于 Repeater 控件，用于显示绑定在该控件上的项目的重复列表。不过，DataList 控件会默认地在数据项目上添加表格。


## 绑定 DataSet 到 DataList 控件

DataList 控件，类似于 Repeater 控件，用于显示绑定在该控件上的项目的重复列表。不过，DataList 控件会默认地在数据项目上添加表格。DataList 控件可被绑定到数据库表、XML 文件或者其他项目列表。在这里，我们将演示如何绑定 XML 文件到 DataList 控件。

在我们的实例中，我们将使用下面的 XML 文件（"cdcatalog.xml"）：

查看这个 XML 文件：cdcatalog.xml

首先，导入 "System.Data" 命名空间。我们需要该命名空间与 DataSet 对象一起工作。 把下面这条指令包含在 .aspx 页面的顶部：

接着，为 XML 文件创建一个 DataSet，并在页面第一次加载时把这个 XML 文件载入 DataSet：

然后我们在 .aspx 页面中创建一个 DataList 控件。<HeaderTemplate> 元素中的内容被首先呈现，并且在输出中仅出现一次，而 <ItemTemplate> 元素中的内容会对应 DataSet 中的每条 "record" 重复出现，最后，<FooterTemplate> 元素中的内容在输出中仅出现一次：

然后我们添加创建 DataSet 的脚本，并且绑定 mycdcatalog DataSet 到 DataList 控件。然后 使用包含表头的 <HeaderTemplate>、包含要显示的数据项的 <ItemTemplate> 和包含文本的 <FooterTemplate> 来填充 DataList 控件。请注意，可设置 DataList 的 gridlines 属性为 "both" 来显示表格边框：


## 实例


## 使用样式

您也可以向 DataList 控件添加样式，让输出更加花哨：


## 实例


## 使用 <AlternatingItemTemplate>

您可以在 <ItemTemplate> 元素后添加 <AlternatingItemTemplate> 元素，用来描述输出中交替行的外观。您可以在 DataList 控件内部对 <AlternatingItemTemplate> 区域的数据添加样式：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebForms DataList` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
