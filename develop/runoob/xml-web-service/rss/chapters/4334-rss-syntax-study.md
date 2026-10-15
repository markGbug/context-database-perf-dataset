# RSS：RSS 语法

- 来源：[RSS 语法](https://www.runoob.com/rss/rss-syntax.html)
- 分类：XML / Web Service
- 技术：RSS
- 笔记类型：学习笔记
- 章节序号：4334

## 本章内容

RSS 2.0 的语法很简单，也很严格。


## RSS 如何工作

RSS 用于在网站间分享信息。

使用 RSS，您在名为聚合器的公司注册您的内容。

步骤之一是，创建一个 RSS 文档，然后使用 .xml 后缀来保存它。然后把此文件上传到您的网站。接下来，通过一个 RSS 聚合器来注册。每天，聚合器都会到被注册的网站搜索 RSS 文档，校验其链接，并显示有关 feed 的信息，这样客户就能够链接到使他们产生兴趣的文档。

提示：请在 RSS 发布 这一节浏览免费的 RSS 聚合器服务。


## RSS 实例

RSS 文档使用一种简单的自我描述的语法。

让我们看一个简单的 RSS 文档：

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
  <item>
    <title>XML 教程</title>
    <link>http://www.runoob.com/xml</link>
    <description>菜鸟教程 XML 教程</description>
  </item>
</channel>

</rss>
```

文档中的第一行：XML 声明 - 定义了文档中使用的 XML 版本和字符编码。此例子遵守 1.0 规范，并使用 UTF-8 字符集(可支持中文)。

下一行是标识此文档是一个 RSS 文档的 RSS 声明（此例是 RSS version 2.0）。

下一行含有 <channel> 元素。此元素用于描述 RSS feed。

<channel> 元素有三个必需的子元素：

- <title> - 定义频道的标题。（比如 菜鸟教程首页）
- <link> - 定义到达频道的超链接。（比如 www.runoob.com）
- <description> - 描述此频道（比如 免费编程教程）

每个 <channel> 元素可拥有一个或多个 <item> 元素。

每个 <item> 元素可定义 RSS feed 中的一篇文章或 "story"。

<item> 元素拥有三个必需的子元素：

- <title> - 定义项目的标题。（比如 RSS 教程）
- <link> - 定义到达项目的超链接。（比如 http://www.runoob.com/rss）
- <description> - 描述此项目（比如 菜鸟教程 Rss 教程）

最后，后面的两行关闭 <channel> 和 <rss> 元素。


## RSS 中的注释

在 RSS 中书写注释的语法与 HTML 的语法类似：

```text
<!-- 这是一个 RSS 注释 -->
```


## RSS 使用 XML 来编写

因为 RSS 也是 XML，请记住：

- 所有的元素必许拥有关闭标签
- 元素对大小写敏感
- 元素必需被正确地嵌套
- 属性值必须带引号


## 复习重点

- 能说明 `RSS 语法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
