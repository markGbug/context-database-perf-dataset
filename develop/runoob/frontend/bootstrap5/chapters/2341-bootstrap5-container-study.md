# Bootstrap5：Bootstrap5 容器

- 来源：[Bootstrap5 容器](https://www.runoob.com/bootstrap5/bootstrap5-container.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：学习笔记
- 章节序号：2341

## 本章内容

在上一章节中我们了解到 Bootstrap 需要一个容器元素来包裹网站的内容。

我们可以使用以下两个容器类：

- .container 类是默认的容器，提供一个固定宽度的布局，宽度会随着屏幕大小的不同而调整。。
- .container-fluid 类用于 100% 宽度，占据全部视口（viewport）的容器，使用这个容器类会始终充满整个屏幕的宽度，适用于全屏布局。。


## 固定宽度

.container 类用于创建固定宽度的响应式页面。

注意：宽度 (max-width) 会根据屏幕宽度同比例放大或缩小。

以下实例中，我们可以尝试调整浏览器窗口的大小来查看容器宽度在不同屏幕中等变化：


## Bootstrap5 .container 实例

```html
<div class="container">
  <h1>我的第一个 Bootstrap 页面</h1>
  <p>这是一些文本。</p>
</div>
```

注意：超级大屏幕 (≥1400px) 是 Bootstrap 5 新增加的， Bootstrap 4 最大的是特大屏幕 (≥1200px)。


## 100% 宽度

.container-fluid 类用于创建一个全屏幕尺寸的容器，容器始终跨越整个屏幕宽度（width 始终为 100%）：


## Bootstrap5 .container-fluid 实例

```html
<div class="container-fluid">
  <h1>我的第一个 Bootstrap 页面</h1>
  <p>使用了 .container-fluid，100% 宽度，占据全部视口（viewport）的容器。</p>
</div>
```


## 容器内边距

默认情况下，容器都有填充左右内边距，顶部和底部没有填充内边距。 Bootstrap 提供了一些间距类用于填充边距。 比如 .pt-5 就是用于填充顶部内边距：


## Bootstrap5 实例

```html
<div class="container pt-5"></div>
```


## 容器的边框和颜色

Bootstrap 也提供了一些边框（border）和颜色（bg-dark、bg-primary等）类用于设置容器的样式：


## Bootstrap5 实例

```html
<div class="container p-5 my-5 border"></div>

<div class="container p-5 my-5 bg-dark text-white"></div>

<div class="container p-5 my-5 bg-primary text-white"></div>
```

后面章节我们会详细说明这些样式。


## 响应式容器

你可以使用 .container-sm|md|lg|xl 类来创建响应式容器。

容器的 max-width 属性值会根据屏幕的大小来改变。


## Bootstrap5 实例

```html
<div class="container-sm">.container-sm</div>
<div class="container-md">.container-md</div>
<div class="container-lg">.container-lg</div>
<div class="container-xl">.container-xl</div>
<div class="container-xxl">.container-xxl</div>
```


## 复习重点

- 能说明 `Bootstrap5 容器` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
