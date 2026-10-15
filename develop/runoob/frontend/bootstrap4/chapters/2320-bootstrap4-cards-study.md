# Bootstrap4：Bootstrap4 卡片

- 来源：[Bootstrap4 卡片](https://www.runoob.com/bootstrap4/bootstrap4-cards.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：学习笔记
- 章节序号：2320

## 本章内容

Bootstrap 4 卡片（Card）组件 是一种灵活且强大的内容容器，可以用于显示各种类型的内容，如文本、图像、列表等。

卡片组件是 Bootstrap 4 中非常常见的 UI 元素，通常用于展示信息、博客文章、产品或社交媒体帖子等。


### 基本结构

卡片组件是由多个嵌套元素组成的，主要包括以下几部分：

- .card：卡片的最外层容器。
- .card-body：包含卡片内容的容器，通常用于放置文本、标题或其他元素。
- .card-title：卡片的标题。
- .card-text：卡片的文本内容。
- .card-img-top 或 .card-img-bottom：用于展示图片，放在卡片的顶部或底部。

样式类说明：


## 简单的卡片

我们可以通过 Bootstrap4 的 .card 与 .card-body 类来创建一个简单的卡片，实例如下:


## 实例

```html
<div class="card">
  <div class="card-body">简单的卡片</div>
</div>
```

Bootstrap4 的卡片类似 Bootstrap 3 中的面板、图片缩略图、well。


## 头部和底部

.card-header类用于创建卡片的头部样式， .card-footer 类用于创建卡片的底部样式：


## 实例

```html
<div class="card">
  <div class="card-header">头部</div>
  <div class="card-body">内容</div>
  <div class="card-footer">底部</div>
</div>
```


## 多种颜色卡片

Bootstrap 4 提供了多种卡片的背景颜色类： .bg-primary, .bg-success, .bg-info, .bg-warning, .bg-danger, .bg-secondary, .bg-dark 和 .bg-light。


## 实例

```html
<div class="container">
  <h2>多种颜色卡片</h2>
  <div class="card">
    <div class="card-body">Basic card</div>
  </div>
  <br>
  <div class="card bg-primary text-white">
    <div class="card-body">Primary card</div>
  </div>
  <br>
  <div class="card bg-success text-white">
    <div class="card-body">Success card</div>
  </div>
  <br>
  <div class="card bg-info text-white">
    <div class="card-body">Info card</div>
  </div>
  <br>
  <div class="card bg-warning text-white">
    <div class="card-body">Warning card</div>
  </div>
  <br>
  <div class="card bg-danger text-white">
    <div class="card-body">Danger card</div>
  </div>
  <br>
  <div class="card bg-secondary text-white">
    <div class="card-body">Secondary card</div>
  </div>
  <br>
  <div class="card bg-dark text-white">
    <div class="card-body">Dark card</div>
  </div>
  <br>
  <div class="card bg-light text-dark">
    <div class="card-body">Light card</div>
  </div>
</div>
```


## 标题、文本和链接

我们可以在头部元素上使用 .card-title 类来设置卡片的标题 。 .card-text 类用于设置卡片正文的内容。 .card-link 类用于给链接设置颜色。


## 实例

```html
<div class="card">
  <div class="card-body">
    <h4 class="card-title">Card title</h4>
    <p class="card-text">Some example text. Some example text.</p>
    <a href="#" class="card-link">Card link</a>
    <a href="#" class="card-link">Another link</a>
  </div>
</div>
```


## 图片卡片

我们可以给 <img> 添加 .card-img-top（图片在文字上方） 或 .card-img-bottom（图片在文字下方 来设置图片卡片：


## 实例

```html
<div class="card" style="width:400px">
  <img class="card-img-top" src="img_avatar1.png" alt="Card image">
  <div class="card-body">
    <h4 class="card-title">John Doe</h4>
    <p class="card-text">Some example text.</p>
    <a href="#" class="btn btn-primary">See Profile</a>
  </div>
</div>
```

如果图片要设置为背景，可以使用 .card-img-overlay 类:


## 实例

```html
<div class="card" style="width:500px">
  <img class="card-img-top" src="img_avatar1.png" alt="Card image">
  <div class="card-img-overlay">
    <h4 class="card-title">John Doe</h4>
    <p class="card-text">Some example text.</p>
    <a href="#" class="btn btn-primary">See Profile</a>
  </div>
</div>
```


## 水平卡片

通过结合网格和工具类，可以以响应式适应移动端的方式将卡片设置为水平排列。

以下实例中，我们使用 .no-gutters 移除网格间距，并使用 .col-md-* 类在 md 屏幕断点处将卡片设置为水平排列。


## 实例


## 复习重点

- 能说明 `Bootstrap4 卡片` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
