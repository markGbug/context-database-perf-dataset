# RSS：RSS 教程

- 来源：[RSS 教程](https://www.runoob.com/rss/rss-tutorial.html)
- 分类：XML / Web Service
- 技术：RSS
- 笔记类型：练习笔记
- 章节序号：4331

## 本章内容

通过使用 RSS，您可以有选择地浏览您感兴趣的以及与您的工作相关的新闻。

通过使用 RSS，您可以把需要的信息从不需要的信息（兜售信息，垃圾邮件等）中分离出来。

通过使用 RSS，您可以创建自己的新闻频道，并将之发布到因特网。

现在开始学习 RSS!


## RSS 文档实例

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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `RSS 教程` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
