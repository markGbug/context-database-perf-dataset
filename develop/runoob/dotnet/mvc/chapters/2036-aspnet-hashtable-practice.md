# MVC：ASP.NET Web Forms - Hashtable 对象

- 来源：[WebForms Hashtable](https://www.runoob.com/aspnet/aspnet-hashtable.html)
- 分类：.NET
- 技术：MVC
- 笔记类型：练习笔记
- 章节序号：2036

## 本章内容

Hashtable 对象包含用键/值对表示的项目。


## 尝试一下 - 实例

Hashtable RadiobuttonList 1

Hashtable RadiobuttonList 2

Hashtable DropDownList


## 创建 Hashtable

Hashtable 对象包含用键/值对表示的项目。键被用作索引，通过搜索键，可以实现对值的快速搜索。

通过 Add() 方法向 Hashtable 添加项目。

下面的代码创建了一个名为 mycountries 的 Hashtable 对象，并添加了四个元素：


## 数据绑定

Hashtable 对象可为下列的控件自动生成文本和值：

- asp:RadioButtonList
- asp:CheckBoxList
- asp:DropDownList
- asp:Listbox

为了绑定数据到 RadioButtonList 控件，首先要在 .aspx 页面中创建一个 RadioButtonList 控件（不带任何 asp:ListItem 元素）：

然后添加创建列表的脚本，并且绑定列表中的值到 RadioButtonList 控件：

然后我们添加一个子例程，当用户点击 RadioButtonList 控件中的某个项目时，该子例程会被执行。当某个单选按钮被点击时，label 中会出现一行文本：


## 实例

注释：您无法选择添加到 Hashtable 的项目的排序方式。如需对项目进行字母排序或者数字排序，请使用 SortedList 对象。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `WebForms Hashtable` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
