# Razor：ASP.NET Web Forms - ArrayList 对象

- 来源：[WebForms ArrayList](https://www.runoob.com/aspnet/aspnet-arraylist.html)
- 分类：.NET
- 技术：Razor
- 笔记类型：学习笔记
- 章节序号：2115

## 本章内容

ArrayList 对象是包含单个数据值的项目的集合。


## 尝试一下 - 实例

ArrayList DropDownList

ArrayList RadioButtonList


## 创建 ArrayList

ArrayList 对象是包含单个数据值的项目的集合。

通过 Add() 方法向 ArrayList 添加项目。

下面的代码创建了一个名为 mycountries 的 ArrayList 对象，并添加了四个项目：

在默认情况下，一个 ArrayList 对象包含 16 个条目。可通过 TrimToSize() 方法把 ArrayList 调整为最终尺寸：

通过 Sort() 方法，ArrayList 也能够按照字母顺序或者数字顺序进行排序：

要实现反向排序，请在 Sort() 方法后应用 Reverse() 方法：


## 绑定数据到 ArrayList

ArrayList 对象可为下列的控件自动生成文本和值：

- asp:RadioButtonList
- asp:CheckBoxList
- asp:DropDownList
- asp:Listbox

为了绑定数据到 RadioButtonList 控件，首先要在 .aspx 页面中创建一个 RadioButtonList 控件（不带任何 asp:ListItem 元素）：

然后添加创建列表的脚本，并且绑定列表中的值到 RadioButtonList 控件：


## 实例

RadioButtonList 控件的 DataSource 属性被设置为该 ArrayList，它定义了这个 RadioButtonList 控件的数据源。RadioButtonList 控件的 DataBind() 方法把 RadioButtonList 控件与数据源绑定在一起。

注释：数据值作为控件的 Text 和 Value 属性来使用。如需添加不同于 Text 的 Value，请使用 Hashtable 对象或者 SortedList 对象。


## 复习重点

- 能说明 `WebForms ArrayList` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
