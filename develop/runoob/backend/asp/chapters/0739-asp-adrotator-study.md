# ASP：ASP AdRotator 组件

- 来源：[ASP AdRotator](https://www.runoob.com/asp/asp-adrotator.html)
- 分类：后端开发
- 技术：ASP
- 笔记类型：学习笔记
- 章节序号：0739

## 本章内容

## ASP AdRotator 组件

每当用户进入网站或刷新页面时，ASP AdRotator 组件就会创建一个 AdRotator 对象来显示一幅不同的图像。有关图像的信息是包含在一个文本文件中。

注释：AdRotator 在 Internet Information Server 7 (IIS7) 中不起作用。


### 语法


## ASP AdRotator 实例

假设我们有一个名为 "ads.txt" 的文件，如下所示：

在上面的文本文件中型号下面的行规定了要显示的图像的名称、超链接地址、图像的替换文本和每百次点击中的显示几率。

上述文本文件的第一行指定当访客点击图像时进行的动作。重定向页（banners.asp）将收到一个带有重定向 URL 的查询字符串。

提示：如需规定图像的高度、宽度和边框，您可以在 REDIRECT 下面插入如下代码：

"banners.asp" 文件如下所示：


## 实例

好了，以上就是全部的内容！


## ASP AdRotator 属性


## ASP AdRotator 方法


## 复习重点

- 能说明 `ASP AdRotator` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
