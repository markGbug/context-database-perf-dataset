# RSS：RSS <channel> 元素

- 来源：[RSS channel 元素](https://www.runoob.com/rss/rss-channel.html)
- 分类：XML / Web Service
- 技术：RSS
- 笔记类型：学习笔记
- 章节序号：4335

## 本章内容

RSS 的 <channel> 元素可描述 RSS feed。


## RSS <channel> 元素

请看下面这个 RSS 文档：

```html
<?xml version="1.0" encoding="UTF-8" ?>
<rss version="2.0">

<channel>
  <title>菜鸟教程首页</title>
  <link>http://www.runoob.com</link>
  <description>免费编程教程</description>
  <item>
    <title>RSS 教程</title>
    <link>http://www.runoob.com/rss</link>
    <description>菜鸟教程 Rss 教程</description>
  </item>
</channel>

</rss>
```

正如前面提到的，<channel> 元素可描述 RSS feed，而拥有三个必需的子元素：

- <title> - 定义频道的标题。（比如 菜鸟教程首页）
- <link> - 定义到达频道的超链接。（比如 http://www.runoob.com）
- <description> - 描述此频道（比如 免费编程教程）

<channel> 通常包含一个或多个 <item> 元素。每个 <item> 元素可定义 RSS feed 中的一篇文章或 "story"。

此外，还存在若干个可选的 <channel> 的子元素。我们会在后面讲解最重要的几个。


## <category> 元素

<category> 子元素用于为 feed 规定种类。

<category> 子元素使 RSS 聚合器基于类别对网站进行分组成为可能。

上面的 RSS 文档的类别可能会是：

```html
<category>Web 开发</category>
```


## <copyright> 元素

<copyright> 子元素会告知有关版本资料的信息。

上面的 RSS 文档的版本可能会是

```html
<copyright>2006 Refsnes Data as. All rights reserved.</copyright>
```


## <image> 元素

<image> 子元素可在聚合器提供某个 feed 时显示一幅图像。

<image> 有三个必需的子元素：

- <url> - 定义引用图像的 URL
- <title> - 定义图像无法被显示时显示的文本
- <link> - 定义到达提供此频道的网站的超链接

上面的 RSS 文档的图像可能是这样的：

```html
<image>
  <url>http://www.runoob.com/images/logo.png</url>
  <title>菜鸟教程</title>
  <link>http://www.runoob.com</link>
</image>
```


## <language> 元素

<language> 子元素用于规定用来编写文档的语言。

<language> 元素使 RSS 聚合器基于语言来对网站进行分组成为可能。

上面的 RSS 文档的语言可能是：

```html
<language>zh-cn</language>
```


## RSS <channel> 参考手册


## 复习重点

- 能说明 `RSS channel 元素` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
