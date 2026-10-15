# RSS：RSS <item> 元素

- 来源：[RSS item 元素](https://www.runoob.com/rss/rss-item.html)
- 分类：XML / Web Service
- 技术：RSS
- 笔记类型：学习笔记
- 章节序号：4336

## 本章内容

每个 <item> 元素可定义 RSS feed 中的一篇文章或 "story"。


## <item> 元素

请看下面的 RSS 文档：

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

正如前面提到的，每个 <item> 元素可定义 RSS feed 中的一篇文章或 story"。

<item> 元素拥有三个必需的子元素：

- <title> - 定义项目的标题。（比如 RSS 教程）
- <link> - 定义到达项目的超链接。（比如 http://www.runoob.com/rss）
- <description> - 描述此项目（比如 菜鸟教程 Rss 教程）

此外，存在若干个 <item> 的可选的子元素，我们会在下面介绍最重要的几个。


## <author> 元素

<author> 子元素用于规定一个项目的作者的电子邮件地址。

注释：为了防止垃圾邮件，一些开发者不会使用这个 <author> 元素。

上面的 RSS 文档中项目的作者可能是：

```html
<author>admin@runoob.com</author>
```


## <comments> 元素

<comments> 子元素允许把一个项目连接到有关此项目的注释。

上面的 RSS 文档中项目的注释可能这样的：

```html
<comments>http://www.runoob.com/comments</comments>
```


## <enclosure> 元素

<enclosure> 子元素允许将一个媒体文件导入一个项中。

<enclosure> 元素有三个必需的属性：

- url - 定义指向此媒体文件的 URL
- length - 定义此媒体文件的长度（字节）
- type - 定义媒体文件的类型

在上面的 RSS 文档中，被包含在项目中的媒体文件可能是这样的：

```html
<enclosure url="http://www.runoob.com/rss/rss.mp3"
length="5000" type="audio/mpeg" />
```


## RSS <item> 参考手册


## 复习重点

- 能说明 `RSS item 元素` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
