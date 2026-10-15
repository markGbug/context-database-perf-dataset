# Bootstrap5：Bootstrap5 下拉菜单

- 来源：[Bootstrap5 下拉菜单](https://www.runoob.com/bootstrap5/bootstrap5-dropdowns.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：练习笔记
- 章节序号：2357

## 本章内容

下拉菜单是可切换的，是以列表格式显示链接的上下文菜单。


## 实例

```html
<div class="dropdown">
  <button type="button" class="btn btn-primary dropdown-toggle" data-bs-toggle="dropdown">
    下拉菜单按钮
  </button>
  <div class="dropdown-menu">
    <a class="dropdown-item" href="#">链接 1</a>
    <a class="dropdown-item" href="#">链接 2</a>
    <a class="dropdown-item" href="#">链接 3</a>
  </div>
</div>
```


### 实例解析

.dropdown 类用来指定一个下拉菜单。

我们可以使用一个按钮或链接来打开下拉菜单， 按钮或链接需要添加 .dropdown-toggle 和 data-toggle="dropdown" 属性。

<div> 元素上添加 .dropdown-menu 类来设置实际下拉菜单，然后在下拉菜单的选项中添加 .dropdown-item 类。


## 下拉菜单中的分割线

.dropdown-divider 类用于在下拉菜单中创建一个水平的分割线：


## 实例

```html
<li><hr class="dropdown-divider"></hr></li>
```


## 下拉菜单中的标题

.dropdown-header 类用于在下拉菜单中添加标题：


## 实例

```html
<li><h5 class="dropdown-header">标题 1</h5></li>
```


## 下拉菜单中的可用项与禁用项

.active 类会让下拉菜单的选项高亮显示 (添加蓝色背景)。

如果要禁用下拉菜单的选项，可以使用.disabled 类。


## 实例

```html
<a class="dropdown-item" href="#">常规项</a>
<a class="dropdown-item active" href="#">激活项</a>
<a class="dropdown-item disabled" href="#">禁用项</a>
```


## 下拉菜单的定位

如果我们想让下拉菜单右对齐，可以在元素上的 .dropdown 类后添加 .dropend 或 .dropstart 类。

.dropend 是右对齐， .dropstart 是左对齐。


## 实例

```html
<!-- 右对齐 -->
<div class="dropdown dropend">
...
</div>

<!-- 左对齐 -->
<div class="dropdown dropstart">
...
</div>
```


## 下拉菜单弹出方向设置

下拉菜单弹出方向默认为向下，当然我们也可以设置不同的方向。


### 指定向右弹出的下拉菜单

如果你希望下拉菜单向右下方弹出，可以在 div 元素上添加 .dropdown-menu-end 类:


## 实例

```html
<!-- 右下方拉菜单按钮 -->
<div class="dropdown dropdown-menu-end">
<button type="button" class="btn btn-primary dropdown-toggle" data-bs-toggle="dropdown">
  下拉菜单右下方弹出
  </button>
  <ul class="dropdown-menu">
    <li><a class="dropdown-item" href="#">链接 1</a></li>
    <li><a class="dropdown-item" href="#">链接 2</a></li>
    <li><a class="dropdown-item" href="#">链接 3</a></li>
  </ul>
</div>
```


### 指定向上弹出的上拉菜单

如果你希望上拉菜单向上弹出，可以在 div 元素上添加 "dropup" 类:


## 实例

```html
<!-- 向上菜单 -->
<div class="dropup">
  <button type="button" class="btn btn-primary dropdown-toggle" data-bs-toggle="dropdown">
    下拉菜单
  </button>
  <ul class="dropdown-menu">
    <li><a class="dropdown-item" href="#">链接 1</a></li>
    <li><a class="dropdown-item" href="#">链接 2</a></li>
    <li><a class="dropdown-item" href="#">链接 3</a></li>
  </ul>
</div>
```


### 指定向左边弹出的下拉菜单

如果你希望下拉菜单向上弹出，可以在 div 元素上添加 dropstart 类:


## 实例

```html
<!-- 左边的下拉菜单 -->
<div class="dropstart">
  添加一些内容，用于测试向左边弹出效果。<button type="button" class="btn btn-primary dropdown-toggle" data-bs-toggle="dropdown">
  下拉菜单
  </button>
  <ul class="dropdown-menu">
    <li><a class="dropdown-item" href="#">链接 1</a></li>
    <li><a class="dropdown-item" href="#">链接 2</a></li>
    <li><a class="dropdown-item" href="#">链接 3</a></li>
  </ul>
</div>
```


## 下拉菜单设置文本

.dropdown-item-text 类可以设置下拉菜单中的文本项：


## 实例

```html
<ul class="dropdown-menu">
  <li><a class="dropdown-item" href="#">链接 1</a></li>
  <li><a class="dropdown-item" href="#">链接 2</a></li>
  <li><a class="dropdown-item" href="#">链接 3</a></li>
  <li><a class="dropdown-item-text" href="#">文本链接</a></li>
  <li><span class="dropdown-item-text">仅仅是文本</span></li>
</ul>
```


## 按钮组中设置下拉菜单

我们可以在按钮中添加下拉菜单：


## 实例

```html
<div class="btn-group">
    <button type="button" class="btn btn-primary">Apple</button>
    <button type="button" class="btn btn-primary">Samsung</button>
    <div class="btn-group">
      <button type="button" class="btn btn-primary dropdown-toggle" data-bs-toggle="dropdown">Sony</button>
      <ul class="dropdown-menu">
        <li><a class="dropdown-item" href="#">Tablet</a></li>
        <li><a class="dropdown-item" href="#">Smartphone</a></li>
      </ul>
    </div>
</div>
```

垂直按钮组带下拉菜单：


## 实例

```html
<div class="btn-group-vertical">
  <button type="button" class="btn btn-primary">Apple</button>
  <button type="button" class="btn btn-primary">Samsung</button>
  <div class="btn-group">
    <button type="button" class="btn btn-primary dropdown-toggle" data-bs-toggle="dropdown">Sony</button>
    <ul class="dropdown-menu">
      <li><a class="dropdown-item" href="#">Tablet</a></li>
      <li><a class="dropdown-item" href="#">Smartphone</a></li>
    </ul>
  </div>
</div>
```


## 导航栏案例


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap5 下拉菜单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
