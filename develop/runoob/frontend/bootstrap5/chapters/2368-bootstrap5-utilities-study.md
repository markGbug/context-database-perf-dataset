# Bootstrap5：Bootstrap5 小工具

- 来源：[Bootstrap5 小工具](https://www.runoob.com/bootstrap5/bootstrap5-utilities.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：学习笔记
- 章节序号：2368

## 本章内容

Bootstrap 5 提供了很多有用的类来帮组我们快速实现效果，不需要重复写一些 CSS 代码。


## 背景颜色

设置不同元素的背景颜色时，需要通过 .text-* 类来设置匹配的文本颜色：


## 实例

```html
<div class="p-3 mb-2 bg-primary text-white">.bg-primary</div>
<div class="p-3 mb-2 bg-secondary text-white">.bg-secondary</div>
<div class="p-3 mb-2 bg-success text-white">.bg-success</div>
<div class="p-3 mb-2 bg-danger text-white">.bg-danger</div>
<div class="p-3 mb-2 bg-warning text-dark">.bg-warning</div>
<div class="p-3 mb-2 bg-info text-dark">.bg-info</div>
<div class="p-3 mb-2 bg-light text-dark">.bg-light</div>
<div class="p-3 mb-2 bg-dark text-white">.bg-dark</div>
<div class="p-3 mb-2 bg-body text-dark">.bg-body</div>
<div class="p-3 mb-2 bg-white text-dark">.bg-white</div>
<div class="p-3 mb-2 bg-transparent text-dark">.bg-transparent</div>
```

.bg-gradient 类可以设置背景颜色渐变的效果：


## 实例

```html
<div class="p-3 mb-2 bg-primary bg-gradient text-white">.bg-primary</div>
<div class="p-3 mb-2 bg-secondary bg-gradient text-white">.bg-secondary</div>
<div class="p-3 mb-2 bg-success bg-gradient text-white">.bg-success</div>
<div class="p-3 mb-2 bg-danger bg-gradient text-white">.bg-danger</div>
<div class="p-3 mb-2 bg-warning bg-gradient text-dark">.bg-warning</div>
<div class="p-3 mb-2 bg-info bg-gradient text-dark">.bg-info</div>
<div class="p-3 mb-2 bg-light bg-gradient text-dark">.bg-light</div>
<div class="p-3 mb-2 bg-dark bg-gradient text-white">.bg-dark</div>
<div class="p-3 mb-2 bg-body bg-gradient text-dark">.bg-body</div>
<div class="p-3 mb-2 bg-white bg-gradient text-dark">.bg-white</div>
<div class="p-3 mb-2 bg-transparent bg-gradient text-dark">.bg-transparent</div>
```


## 边框

我们可以使用 border 相关类根据需要显示边框：


## 实例

```html
<span class="border"></span>
<span class="border border-0"></span>
<span class="border border-top-0"></span>
<span class="border border-end-0"></span>
<span class="border border-bottom-0"></span>
<span class="border border-start-0"></span>
<br>

<span class="border-top"></span>
<span class="border-end"></span>
<span class="border-bottom"></span>
<span class="border-start"></span>
```

.border-1 到 .border-5 类用于设置边框线条的宽度：


## 实例

```html
<span class="border border-1"></span>
<span class="border border-2"></span>
<span class="border border-3"></span>
<span class="border border-4"></span>
<span class="border border-5"></span>
```

以下设置了边框的不同颜色：


## 实例

```html
<span class="border border-primary"></span>
<span class="border border-secondary"></span>
<span class="border border-success"></span>
<span class="border border-danger"></span>
<span class="border border-warning"></span>
<span class="border border-info"></span>
<span class="border border-light"></span>
<span class="border border-dark"></span>
<span class="border border-white"></span>
```

rounded 相关类用于设置圆角：


## 实例

```html
<img src="..." class="rounded" alt="...">
<img src="..." class="rounded-top" alt="...">
<img src="..." class="rounded-end" alt="...">
<img src="..." class="rounded-bottom" alt="...">
<img src="..." class="rounded-start" alt="...">
<img src="..." class="rounded-circle" alt="...">
<img src="..." class="rounded-pill" alt="...">
```

rounded-0 到 rounded-3 类用于设置圆角的大小：


## 实例

```html
<img src="..." class="rounded-0" alt="...">
<img src="..." class="rounded-1" alt="...">
<img src="..." class="rounded-2" alt="...">
<img src="..." class="rounded-3" alt="...">
```


## 浮动与清除浮动

元素向右浮动使用 .float-end 类，向左浮动使用 .float-start 类， .clearfix 类用于清除浮动:


## 实例

```html
<div class="clearfix">
  <span class="float-start">Float left</span>
  <span class="float-end">Float right</span>
</div>
```

也可以根据屏幕尺寸来设置浮动效果(.float-*-left|right - * 表示 sm (>=576px), md (>=768px), lg (>=992px), xl (>=1200px) or xxl (>=1400px)):


## 实例

```html
<div class="float-sm-end">小屏幕向右浮动</div><br>
<div class="float-md-end">中等屏幕向右浮动</div><br>
<div class="float-lg-end">大屏幕向右浮动</div><br>
<div class="float-xl-end">超大屏幕向右浮动</div><br>
<div class="float-xxl-end">特大屏幕向右浮动</div><br>
<div class="float-none">没有浮动</div>
```


## 居中对齐


## 复习重点

- 能说明 `Bootstrap5 小工具` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
