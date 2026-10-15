# ASP：ASP Content Rotator 组件 (ASP 3.0)

- 来源：[ASP Content Rotator](https://www.runoob.com/asp/asp-contentrotator.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：概念卡
- 章节序号：0742

## 本章内容

## ASP Content Rotator 组件

ASP Content Rotator 组件创建一个 ContentRotator 对象，每当访客进入网站或刷新页面时，该对象就会显示一段不同的内容字符串。

有关内容字符串的信息是包含在一个名为内容目录文件（Content Schedule File）的文本文件中。

内容字符串可包含 HTML 标签，这样您就可以显示 HTML 可呈现的任何类型的内容：文本、图像、颜色或者超链接。


### 语法


## ASP Content Rotator 实例

每当访客浏览网页时，下面的实例就会显示不同的内容。

首先，创建一个名为 "textads.txt" 的文本文件，并把它放置在名为 "text" 的子文件夹中。

"textads.txt":

请注意在每个内容字符串起始位置的 # 号码。这个号码是一个可选的参数，用来指示 HTML 内容字符串的相对权重。在上面的文本文件中，Content Rotator 有十分之三的几率显示第一个内容字符串，有十分之三的几率显示第二个内容字符串，有十分之四的几率显示第三个字符串。

然后，创建一个 ASP 文件，并插入下面的代码：


## 实例


## ASP Content Rotator 组件的方法

输出：


## This is a great day!!

Visit RUNOOB


## 记忆卡片

- 一句话定义：`ASP Content Rotator` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
