# HTML：HTML5 简介

- 来源：[HTML5 教程](https://www.runoob.com/html/html5-intro.html)
- 分类：前端开发
- 技术：HTML
- 笔记类型：学习笔记
- 章节序号：2631

## 本章内容

HTML5是HTML最新的修订版本，2014年10月由万维网联盟（W3C）完成标准制定。

HTML5的设计目的是为了在移动设备上支持多媒体。

HTML5 简单易学。


## 什么是 HTML5?

HTML5 是下一代 HTML 标准。

HTML , HTML 4.01的上一个版本诞生于 1999 年。自从那以后，Web 世界已经经历了巨变。

HTML5 仍处于完善之中。然而，大部分现代浏览器已经具备了某些 HTML5 支持。


## HTML5 是如何起步的？

HTML5 是 W3C 与 WHATWG 合作的结果,WHATWG 指 Web Hypertext Application Technology Working Group。

WHATWG 致力于 web 表单和应用程序，而 W3C 专注于 XHTML 2.0。在 2006 年，双方决定进行合作，来创建一个新版本的 HTML。

HTML5 中的一些有趣的新特性：

- 用于绘画的 canvas 元素
- 用于媒介回放的 video 和 audio 元素
- 对本地离线存储的更好的支持
- 新的特殊内容元素，比如 article、footer、header、nav、section
- 新的表单控件，比如 calendar、date、time、email、url、search


## HTML5 <!DOCTYPE>

<!doctype> 声明必须位于 HTML5 文档中的第一行,使用非常简单:

```text
<!DOCTYPE html>
```


## 最小的HTML5文档

下面是一个简单的HTML5文档：

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>文档标题</title>
</head>

<body>
文档内容......
</body>

</html>
```

注意：对于中文网页需要使用 <meta charset="utf-8"> 声明编码，否则会出现乱码。


## HTML5 的改进

- 新元素
- 新属性
- 完全支持 CSS3
- Video 和 Audio
- 2D/3D 制图
- 本地存储
- 本地 SQL 数据
- Web 应用


## HTML5 多媒体

使用 HTML5 你可以简单的在网页中播放 视频(video)与音频 (audio) 。

- HTML5 <video>
- HTML5 <audio>


## HTML5 应用

使用 HTML5 你可以简单地开发应用

- 本地数据存储
- 访问本地文件
- 本地 SQL 数据
- 缓存引用
- Javascript 工作者
- XHTMLHttpRequest 2


## HTML5 图形

使用 HTML5 你可以简单的绘制图形:

- 使用 <canvas> 元素。
- 使用内联 SVG。
- 使用 CSS3 2D 转换、CSS3 3D 转换。


## HTML5 使用 CSS3

- 新选择器
- 新属性
- 动画
- 2D/3D 转换
- 圆角
- 阴影效果
- 可下载的字体

了解更多CSS3知识请查看本站的 CSS3 教程。


## 语义元素

HTML5 添加了很多语义元素如下所示：


## HTML5 表单

新表单元素, 新属性，新输入类型，自动验证。


## 已移除元素

以下的 HTML 4.01 元素在HTML5中已经被删除:

- <acronym>
- <applet>
- <basefont>
- <big>
- <center>
- <dir>
- <font>
- <frame>
- <frameset>
- <noframes>
- <strike>


## 每一章中的实例

通过我们的 HTML 编辑器，您能够编辑 HTML，然后点击按钮来查看结果。


## 实例

```html
<!DOCTYPE HTML>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<video width="320" height="240" controls>
  <source src="movie.mp4" type="video/mp4">
  <source src="movie.ogg" type="video/ogg">
  你的浏览器不支持 video 标签。
</video>

</body>
</html>
```

点击 "尝试一下" 按钮查看在线运行结果。


## HTML5 浏览器支持

最新版本的 Safari、Chrome、Firefox 以及 Opera 支持某些 HTML5 特性。Internet Explorer 9 将支持某些 HTML5 特性。

IE9 以下版本浏览器兼容HTML5的方法，使用本站的静态资源的html5shiv包：

```html
<!--[if lt IE 9]>
    <script src="https://lf9-cdn-tos.bytecdntp.com/cdn/expire-1-M/html5shiv/3.7.3/html5shiv.min.js"></script>
<![endif]-->
```

载入后，初始化新标签的CSS：

```text
/*html5*/
article,aside,dialog,footer,header,section,nav,figure,menu{display:block}
```


## HTML5 参考手册

在本站中你可以找到关于HTML5 的标签及属性描述，详细请点击 HTML5参考手册。


## 复习重点

- 能说明 `HTML5 教程` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
