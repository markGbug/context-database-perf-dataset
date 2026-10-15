# jQuery：jQuery 安装

- 来源：[jQuery 安装](https://www.runoob.com/jquery/jquery-install.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：练习笔记
- 章节序号：2964

## 本章内容

## 网页中添加 jQuery

可以通过多种方法在网页中添加 jQuery。 您可以使用以下方法：

- 从 jquery.com 下载 jQuery 库
- 从 CDN 中载入 jQuery, 如从 Google 中加载 jQuery


## 下载 jQuery

有两个版本的 jQuery 可供下载：

- Production version - 用于实际的网站中，已被精简和压缩。
- Development version - 用于测试和开发（未压缩，是可读的代码）

以上两个版本都可以从 jquery.com 中下载。

jQuery 库是一个 JavaScript 文件，您可以使用 HTML 的 <script> 标签引用它：

```html
<head>
<script src="jquery-1.10.2.min.js"></script>
</head>
```

提示： 将下载的文件放在网页的同一目录下，就可以使用jQuery。


## 替代方案

如果您不希望下载并存放 jQuery，那么也可以通过 CDN（内容分发网络） 引用它。

Staticfile CDN、百度、又拍云、新浪、谷歌和微软的服务器都存有 jQuery 。

如果你的站点用户是国内的，建议使用百度、又拍云、新浪等国内CDN地址，如果你站点用户是国外的可以使用谷歌和微软。

注：本站实例均采用菜鸟教程 CDN 库。

如需从 Staticfile CDN、又拍云、新浪、谷歌或微软引用 jQuery，请使用以下代码之一：


## 百度 CDN:

```html
<head>
<script src="https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js">
</script>
</head>
```


## CDNJS:

```html
<head>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.3/jquery.min.js">
</script>
</head>
```


## 又拍云 CDN:

```html
<head>
<script src="https://upcdn.b0.upaiyun.com/libs/jquery/jquery-2.0.2.min.js">
</script>
</head>
```


## Staticfile CDN:

```html
<head>
<script src="https://cdn.staticfile.net/jquery/1.10.2/jquery.min.js">
</script>
</head>
```


## Google CDN:

```html
<head>
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js">
</script>
</head>
```


## Microsoft CDN:

```html
<head>
<script src="https://ajax.aspnetcdn.com/ajax/jquery/jquery-1.9.0.min.js"></script>
</head>
```


## jQuery 使用版本

我们可以在浏览器的 Console 窗口中使用 $.fn.jquery 命令查看当前 jQuery 使用的版本：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery 安装` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
