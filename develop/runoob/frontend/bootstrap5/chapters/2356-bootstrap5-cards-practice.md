# Bootstrap5：Bootstrap5 卡片

- 来源：[Bootstrap5 卡片](https://www.runoob.com/bootstrap5/bootstrap5-cards.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：练习笔记
- 章节序号：2356

## 本章内容

Bootstrap 5 卡片（Card）组件 是一种强大且灵活的容器，用于展示各种内容，如文本、图片、列表、按钮等。

卡片组件在 Bootstrap 5 中得到了改进和增强，提供了更多的定制选项和更灵活的布局方式。

卡片组件在 UI 设计中非常常见，尤其适用于博客、社交媒体、仪表盘和其他内容展示页面。


### 本结构

Bootstrap 5 的卡片组件包括以下常用元素：

- .card：卡片的最外层容器。
- .card-body：卡片的主要内容区域。
- .card-title：卡片的标题部分。
- .card-text：卡片的文本部分。
- .card-img-top 或 .card-img-bottom：卡片顶部或底部的图片。

卡片样式类说明：


## 简单的卡片

我们可以通过 Bootstrap5 的 .card 与 .card-body 类来创建一个简单的卡片，卡片可以包含头部、内容、底部以及各种颜色设置，实例如下:


## 实例

```html
<div class="card">
  <div class="card-body">简单的卡片</div>
</div>
```


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

Bootstrap 5 提供了多种卡片的背景颜色类： .bg-primary, .bg-success, .bg-info, .bg-warning, .bg-danger, .bg-secondary, .bg-dark 和 .bg-light。


## 实例

```html
<div class="container">
  <h2>多种颜色卡片</h2>
  <div class="card">
    <div class="card-body">基础卡片</div>
  </div>
  <br>
  <div class="card bg-primary text-white">
    <div class="card-body">主要卡片</div>
  </div>
  <br>
  <div class="card bg-success text-white">
    <div class="card-body">成功卡片</div>
  </div>
  <br>
  <div class="card bg-info text-white">
    <div class="card-body">信息卡片</div>
  </div>
  <br>
  <div class="card bg-warning text-white">
    <div class="card-body">警告卡片</div>
  </div>
  <br>
  <div class="card bg-danger text-white">
    <div class="card-body">危险卡片</div>
  </div>
  <br>
  <div class="card bg-secondary text-white">
    <div class="card-body">次要卡片</div>
  </div>
  <br>
  <div class="card bg-dark text-white">
    <div class="card-body">黑色卡片</div>
  </div>
  <br>
  <div class="card bg-light text-dark">
    <div class="card-body">浅色卡片</div>
  </div>
</div>
```


## 标题、文本和链接

我们可以在头部元素上使用 .card-title 类来设置卡片的标题 。 .card-body 类用于设置卡片正文的内容。.card-text 类用于设置卡 .card-body 类中的 <p> 标签，如果说最后一行可以移除底部边距。 .card-link 类用于给链接设置颜色。


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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap5 卡片` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
