# ASP：ASP Content Linking 组件

- 来源：[ASP Content Linking](https://www.runoob.com/asp/asp-contentlinking.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：学习笔记
- 章节序号：0741

## 本章内容

## 尝试一下 - 实例

Content Linking 组件 本例构建一个内容列表。

Content Linking 组件 2 本例使用 Content Linking 组件在一个文本文件所列的页面间进行导航。


## ASP Content Linking 组件

ASP Content Linking 组件用于创建快捷便利的导航系统！

Content Linking 组件会返回一个 Nextlink 对象，这个对象用于容纳需要导航网页的一个列表。


### 语法


## ASP Content Linking 实例

首先，我们会创建一个文本文件 - "links.txt"：

上面的文本文件包含需要导航的页面。页面的排列顺序应该与它们的显示顺序相同，并包含对每个文件名的描述（使用制表符来分隔文件名和描述信息）。

注释：如果您希望向列表添加页面，或者改变在列表中的页面顺序，那么您需要做的仅仅是修改这个文本文件而已！导航会自动更新！

然后我们创建一个引用文件，"nlcode.inc"。.inc 文件创建一个 NextLink 对象来在 "links.txt" 中列出的页面间进行导航。

"nlcode.inc":

请在文本文件 "links.txt" 列出的每个 .asp 页面中放置一行代码：<!-- #include file="nlcode.inc"-->。这行代码会在 "links.txt" 中列出每个页面上引用 "nlcode.inc" 中的代码，这样导航就可以工作了。


## ASP Content Linking 组件的方法

输出：

There are 4 items in the list

输出：

Item number 3

输出：

Next description is: ASP Variables

输出：

Next URL is: asp_variables.asp

输出：

Third description is: ASP Variables

输出：

Third URL is: asp_variables.asp

输出：

Previous description is: ASP Variables

输出：

Previous URL is: asp_variables.asp


## 复习重点

- 能说明 `ASP Content Linking` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
