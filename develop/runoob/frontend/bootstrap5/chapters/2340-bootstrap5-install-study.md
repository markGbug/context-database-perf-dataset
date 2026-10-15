# Bootstrap5：Bootstrap5 安装使用

- 来源：[Bootstrap5 安装使用](https://www.runoob.com/bootstrap5/bootstrap5-install.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：学习笔记
- 章节序号：2340

## 本章内容

我们可以通过以下两种方式来安装 Bootstrap5：

- 使用 Bootstrap5 CDN。
- 从官网 getbootstrap.com 下载 Bootstrap 5。


### Bootstrap 5 CDN

CDNJS：


## Bootstrap5 CDN

```html
<!-- 新 Bootstrap5 核心 CSS 文件 -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/5.1.3/css/bootstrap.min.css">

<!--  popper.min.js 用于弹窗、提示、下拉菜单 -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/2.11.2/umd/popper.min.js"></script>

<!-- 最新的 Bootstrap5 核心 JavaScript 文件 -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/twitter-bootstrap/5.1.3/js/bootstrap.min.js"></script>
```

注意：popper.min.js 用于设置弹窗、提示、下拉菜单。

bootstrap.bundle.js （未压缩版）或 bootstrap.bundle.min.js（压缩版） 包含了捆绑的插件如 popper.min.js 及其他依赖脚本，所以我们也可以直接使用以下代码：


## 实例


## Bootstrap5 CDN（jsDelivr）

```html
<!-- 新 Bootstrap5 核心 CSS 文件 -->
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css" crossorigin="anonymous">
<!-- 最新的 Bootstrap5 核心 JavaScript 文件 -->
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bundle.min.js" crossorigin="anonymous"></script>
```


## Bootstrap5 CDN（Staticfile）

此外，你还可以使用以下的 CDN 服务：

- 国内推荐使用 1：https://cdn.bytedance.com/
- 国内推荐使用 2：https://www.staticfile.net/
- 国际推荐使用：https://cdnjs.com/


### 下载 Bootstrap 5

你可以去官网 https://getbootstrap.com/ 下载 Bootstrap5 资源库。

注：此外你还可以通过包的管理工具 npm、 yarn、gem、 composer 等来安装：

```text
npm install bootstrap
```

```text
yarn add bootstrap
```

```text
gem install bootstrap -v 5.1.1
```

```text
composer require twbs/bootstrap:5.1.1
```


## 创建第一个 Bootstrap 5 页面


### 1、添加 HTML5 doctype

Bootstrap 要求使用 HTML5 文件类型，所以需要添加 HTML5 doctype 声明。

HTML5 doctype 在文档头部声明，并设置对应编码:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
  </head>
</html>
```


### 移动设备优先

为了让 Bootstrap 开发的网站对移动设备友好，确保适当的绘制和触屏缩放，需要在网页的 head 之中添加 viewport meta 标签，如下所示：

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

width=device-width 表示宽度是设备屏幕的宽度。

initial-scale=1 表示初始的缩放比例。


## 容器类

Bootstrap 5 需要一个容器元素来包裹网站的内容。

我们可以使用以下两个容器类：

- .container 类用于固定宽度并支持响应式布局的容器。
- .container-fluid 类用于 100% 宽度，占据全部视口（viewport）的容器。


## 两个 Bootstrap 5 页面


## Bootstrap5 .container 实例

```html
<div class="container">
  <h1>我的第一个 Bootstrap 页面</h1>
  <p>这是一些文本。</p>
</div>
```

以下实例展示了占据全部视口（viewport）的容器。


## Bootstrap5 .container-fluid 实例

```html
<div class="container-fluid">
  <h1>我的第一个 Bootstrap 页面</h1>
  <p>使用了 .container-fluid，100% 宽度，占据全部视口（viewport）的容器。</p>
</div>
```


## 复习重点

- 能说明 `Bootstrap5 安装使用` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
