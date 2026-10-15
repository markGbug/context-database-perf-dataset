# Bootstrap5：Bootstrap5 列表组

- 来源：[Bootstrap5 列表组](https://www.runoob.com/bootstrap5/bootstrap5-list-groups.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：练习笔记
- 章节序号：2355

## 本章内容

Bootstrap 5 列表组（List Group） 是一种用于展示一系列项目或内容的组件，通常用于展示导航、标签、菜单或其他类似的列表形式。

列表组组件提供了一个灵活的方式来展示有序或无序的内容，可以自定义每个项目的样式、交互和布局。


### 基本结构

Bootstrap 5 列表组由以下几部分组成：

- .list-group：用于包裹整个列表的容器。
- .list-group-item：每个列表项，通常包含文本、链接或其他内容。
- .list-group-item-action：使列表项变得可点击，常用于创建可交互的列表。
- .list-group-item-primary 等：用于为列表项添加不同的背景色或其他样式。

大部分基础列表组都是无序的。

要创建列表组，可以在 <ul> 元素上添加 .list-group 类, 在 <li> 元素上添加 .list-group-item 类:


## 实例

```html
<ul class="list-group">
  <li class="list-group-item">第一项</li>
  <li class="list-group-item">第二项</li>
  <li class="list-group-item">第三项</li>
</ul>
```


## 激活状态的列表项

通过添加 .active 类来设置激活状态的列表项：


## 实例

```html
<ul class="list-group">
  <li class="list-group-item active">激活列表项</li>
  <li class="list-group-item">第二项</li>
  <li class="list-group-item">第三项</li>
</ul>
```


## 禁用的列表项

.disabled 类用于设置禁用的列表项:


## 实例

```html
<ul class="list-group">
  <li class="list-group-item disabled">禁用项</li>
  <li class="list-group-item">第二项</li>
  <li class="list-group-item">第三项</li>
</ul>
```


## 链接列表项

要创建一个链接的列表项，可以将 <ul> 替换为 <div> ， <a> 替换 <li>。如果你想鼠标悬停显示灰色背景就添加.list-group-item-action 类:


## 实例

```html
<div class="list-group">
  <a href="#" class="list-group-item list-group-item-action">第一项</a>
  <a href="#" class="list-group-item list-group-item-action">第二项</a>
  <a href="#" class="list-group-item list-group-item-action">第三项</a>
</div>
```


## 移除列表边框

使用 .list-group-flush 类来删除列表的边框和圆角：


## 实例

```html
<ul class="list-group list-group-flush">
  <li class="list-group-item">第一项</li>
  <li class="list-group-item">第二项</li>
  <li class="list-group-item">第三项</li>
  <li class="list-group-item">第四项</li>
</ul>
```


## 水平列表组

我们可以将 .list-group-horizontal 类添加到 .list-group 类后面来创建水平列表组：


## 实例

```html
<ul class="list-group list-group-horizontal">
  <li class="list-group-item">第一项</li>
  <li class="list-group-item">第二项</li>
  <li class="list-group-item">第三项</li>
  <li class="list-group-item">第四项</li>
</ul>
```


## 多种颜色列表项

列表项目的颜色可以通过以下列来设置： .list-group-item-success, list-group-item-secondary, list-group-item-info, list-group-item-warning, .list-group-item-danger, list-group-item-dark 和 list-group-item-light:


## 实例

```html
<ul class="list-group">
  <li class="list-group-item list-group-item-success">成功列表项</li>
  <li class="list-group-item list-group-item-secondary">次要列表项</li>
  <li class="list-group-item list-group-item-info">信息列表项</li>
  <li class="list-group-item list-group-item-warning">警告列表项</li>
  <li class="list-group-item list-group-item-danger">危险列表项</li>
  <li class="list-group-item list-group-item-primary">主要列表项</li>
  <li class="list-group-item list-group-item-dark">深灰色列表项</li>
  <li class="list-group-item list-group-item-light">浅色列表项</li>
</ul>
```


### 链接的多种颜色列表项


## 实例

```html
<div class="list-group">
    <a href="#" class="list-group-item list-group-item-action">激活列表项</a>
    <a href="#" class="list-group-item list-group-item-success">成功列表项</a>
    <a href="#" class="list-group-item list-group-item-secondary">次要列表项</a>
    <a href="#" class="list-group-item list-group-item-info">信息列表项</a>
    <a href="#" class="list-group-item list-group-item-warning">警告列表项</a>
    <a href="#" class="list-group-item list-group-item-danger">危险列表项</a>
    <a href="#" class="list-group-item list-group-item-primary">主要列表项</a>
    <a href="#" class="list-group-item list-group-item-dark">深灰色列表项</a>
    <a href="#" class="list-group-item list-group-item-light">浅色列表项</a>
</div>
```


## 列表组案例


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap5 列表组` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
