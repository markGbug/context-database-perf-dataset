# Bootstrap4：Bootstrap4 小工具

- 来源：[Bootstrap4 小工具](https://www.runoob.com/bootstrap4/bootstrap4-utilities.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：学习笔记
- 章节序号：2335

## 本章内容

Bootstrap4 提供了一些小工具，可以让我们不用写 CSS 代码就能实现想要的效果。


## 边框

使用 border 类可以添加或移除边框:


## 实例

```html
<span class="border"></span>
<span class="border border-0"></span>
<span class="border border-top-0"></span>
<span class="border border-right-0"></span>
<span class="border border-bottom-0"></span>
<span class="border border-left-0"></span>
```


## 边框颜色

Bootstrap4 提供了一些类来设置边框颜色:


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


## 边框圆角设置

使用rounded 类可以添加圆角边框:


## 实例

```html
<span class="rounded"></span>
<span class="rounded-top"></span>
<span class="rounded-right"></span>
<span class="rounded-bottom"></span>
<span class="rounded-left"></span>
<span class="rounded-circle"></span>
<span class="rounded-0"></span>
```


## 浮动

.float-right 类用于设置元素右浮动， .float-left 设置元素左浮动, .clearfix 类用于清除浮动:


## 实例

```html
<div class="clearfix">
  <span class="float-left">左浮动</span>
  <span class="float-right">右浮动</span>
</div>
```


## 响应式浮动

我们看可以设置浮动 (.float-*-left|right - * 为 sm, md, lg 或 xl)的方向依赖于屏幕的大小:


## 实例

```html
<div class="float-sm-right">在大于小屏幕尺寸上右浮动</div><br>
<div class="float-md-right">在大于中等屏幕尺寸上右浮动</div><br>
<div class="float-lg-right">在大于大屏幕尺寸上右浮动</div><br>
<div class="float-xl-right">在大于超大屏幕尺寸上右浮动</div><br>
<div class="float-none">没有浮动</div>
```


## 居中对齐

使用 .mx-auto 类来设置居中对齐:


## 实例

```html
<div class="mx-auto bg-warning" style="width:150px">居中显示</div>
```


## 宽度

元素上使用 w-* 类 (.w-25, .w-50, .w-75, .w-100, .mw-100) 来设置宽度:


## 实例

```html
<div class="w-25 bg-warning">宽度 25%</div>
<div class="w-50 bg-warning">宽度 50%</div>
<div class="w-75 bg-warning">宽度 75%</div>
<div class="w-100 bg-warning">宽度 100%</div>
<div class="mw-100 bg-warning">最大宽度 100%</div>
```


## 高度

元素上使用 h-* 类 (.h-25, .h-50, .h-75, .h-100, .mh-100) 来设置高度:


## 实例

```html
<div style="height:200px;background-color:#ddd">
    <div class="h-25 bg-warning">高度 25%</div>
    <div class="h-50 bg-warning">高度 50%</div>
    <div class="h-75 bg-warning">高度 75%</div>
    <div class="h-100 bg-warning">高度 100%</div>
    <div class="mh-100 bg-warning" style="height:500px">最大高度 100%</div>
</div>
```


## 间距

间距设置语法如下:

```text
{property}{sides}-{size}  // 适用 xs(<=576px)
{property}{sides}-{breakpoint}-{size} // 适用 sm (>=576px), md (>=768px), lg (>=992px), xl (>=1200px)
```

breakpoints 指的是屏幕宽度: xs (<=576px), sm (>=576px), md (>=768px), lg (>=992px), xl (>=1200px)。

property 代表属性，包含：

- m - 用来设置 margin
- p - 用来设置 padding

sides 主要指方向：

- t - 用来设置 margin-top 或 padding-top
- b - 用来设置 margin-bottom 或 padding-bottom
- l - 用来设置 margin-left 或 padding-left
- r - 用来设置 margin-right 或 padding-right
- x - 用来设置 *-left 和 *-right
- y - 用来设置 *-top 和 *-bottom
- blank - 用来设置元素在四个方向的 margin 或 padding

size 指的是边距的大小：

- 0 - 设置 margin 或 padding 为 0
- 1 - 设置 margin 或 padding 为 $spacer * .25
- 2 - 设置 margin 或 padding 为 $spacer * .5
- 3 - 设置 margin 或 padding 为 $spacer
- 4 - 设置margin 或 padding 为 $spacer * 1.5
- 5 - 设置 margin 或 padding 为 $spacer * 3
- auto - 设置 margin 为 auto

外边距 margin 可以设置负数，在数字前面添加字母 "n" :

- n1 - 设置 margin 为 -.25rem (如果 font-size 为 16px 则为 -4px )
- n2 - 设置 margin 为 -.5rem (如果 font-size 为 16px 则为 -8px)
- n3 - 设置 margin 为 -1rem (如果 font-size 为 16px 则为 -16px)
- n4 - 设置 margin 为 -1.5rem (如果 font-size 为 16px 则为 -24px)
- n5 - 设置 margin 为 -3rem (如果 font-size 为 16px 则为 -48px)


## 实例

```html
<div class="mx-auto" style="width: 200px;">
  元素设置居中
</div>

<form >
    <div class="form-row">
        <div class="form-group">

        <label for="text" class="mt-2">设置 margin-top：</label>
        <input type="text" class="form-control" id="text" placeholder="email">

        <label for="color" class="mt-2">颜色：</label>
        <input type="color" id="color" class="form-control" style="width: 60px;padding: 4px;" autocomplete="off" value="#656565">
        </div>
    </div>
</form>
```


### 更多实例


## 复习重点

- 能说明 `Bootstrap4 小工具` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
