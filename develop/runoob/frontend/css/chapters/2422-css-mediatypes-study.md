# CSS：CSS 媒体类型

- 来源：[CSS 媒体类型](https://www.runoob.com/css/css-mediatypes.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：学习笔记
- 章节序号：2422

## 本章内容

媒体类型允许你指定文件将如何在不同媒体呈现。该文件可以以不同的方式显示在屏幕上，在纸张上，或听觉浏览器等等。


## 媒体类型

一些 CSS 属性只设计了某些媒体。例如 voice-family 属性是专为听觉用户代理。其他一些属性可用于不同的媒体类型。例如， font-size 属性可用于屏幕和印刷媒体，但有不同的值。屏幕和纸上的文件不同，通常需要一个更大的字体，sans-serif 字体比较适合在屏幕上阅读，而 serif 字体更容易在纸上阅读。


## @media 规则

@media 规则允许在相同样式表为不同媒体设置不同的样式。

在下面的例子告诉我们浏览器屏幕上显示一个 14 像素的 Verdana 字体样式。但是如果页面打印，将是 10 个像素的 Times 字体。请注意，font-weight 在屏幕上和纸上设置为粗体：


## 实例

```text
@media screen
{
    p.test {font-family:verdana,sans-serif;font-size:14px;}
}
@media print
{
    p.test {font-family:times,serif;font-size:10px;}
}
@media screen,print
{
    p.test {font-weight:bold;}
}
```

你可以自己尝试看看 ! 如果您使用的是 Mozilla / Firefox 或 IE5+ 打印此页，你会看到，媒体类型将使用另一种比其他文本字体大小小点的字体显示。


## 其他媒体类型

注意：媒体类型名称不区分大小写。


## 复习重点

- 能说明 `CSS 媒体类型` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
