# Highcharts：Highcharts 环境配置

- 来源：[Highcharts 环境配置](https://www.runoob.com/highcharts/highcharts-setup.html)
- 分类：前端开发
- 技术：Highcharts
- 笔记类型：练习笔记
- 章节序号：2572

## 本章内容

本章节我们将为大家介绍如何在网页中使用 Highcharts。

本教程将 Highcharts 与 jQuery 结合使用，所以在加载 Highcharts 前必须先加载 jQuery 库。

如果你对 jQuery 不熟悉，可以参阅本站的jQuery 教程。


## 安装 jQuery

jQuery 安装可以使用以下两种方式：

- 1、访问 jquery.com 下载jQuery包。
- 2、使用 Staticfile CDN 静态资源库的jQuery资源：https://cdn.staticfile.net/jquery/2.1.4/jquery.min.js
- 3、使用百度静态资源库的jQuery资源：https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js


### 使用下载的方式

使用下载的方式，在 HTML 页面引入 jQuery 代码:

```html
<head>
   <script src="/jquery/jquery.min.js"></script>
</head>
```


### 使用 CDN（推荐）

使用 Staticfile CDN 静态资源库来加载jQuery库：

```html
<head>
   <script src="https://cdn.staticfile.net/jquery/2.1.4/jquery.min.js"></script>
</head>
```


## 安装 Highcharts

Highcharts 安装可以使用以下两种方式：

- 1、访问 highcharts.com 下载 Highcharts 包。
- 2、使用官方提供的 CDN 地址：https://code.highcharts.com/highcharts.js


### 使用下载的方式（推荐）

使用下载的方式，在 HTML 页面引入 Highcharts 代码:

```html
<head>
   <script src="/highcharts/highcharts.js"></script>
</head>
```


### 使用 CDN

使用官方提供的 CDN 地址：

```html
<head>
   <script src="https://code.highcharts.com/highcharts.js"></script>
</head>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Highcharts 环境配置` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
