# Bootstrap4：Bootstrap4 滚动监听(Scrollspy)

- 来源：[Bootstrap4 滚动监听](https://www.runoob.com/bootstrap4/bootstrap4-scrollspy.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：学习笔记
- 章节序号：2334

## 本章内容

滚动监听（Scrollspy）插件，即自动更新导航插件，会根据滚动条的位置自动更新对应的导航目标。其基本的实现是随着您的滚动。


## 如何创建滚动监听

以下实例演示了如何创建滚动监听：


## 实例

```java
<!-- 可滚动区域 -->
<body data-spy="scroll" data-target=".navbar" data-offset="50">

<!-- The navbar - The <a> elements are used to jump to a section in the scrollable area -->
<nav class="navbar navbar-expand-sm bg-dark navbar-dark fixed-top">
...
  <ul class="navbar-nav">
    <li><a href="#section1">Section 1</a></li>
    ...
</nav>

<!-- 第一部分内容 -->
<div id="section1">
  <h1>Section 1</h1>
  <p>Try to scroll this page and look at the navigation bar while scrolling!</p>
</div>
...

</body>
```


### 实例解析

向您想要监听的元素（通常是 body）添加 data-spy="scroll" 。

然后添加 data-target 属性，它的值为导航栏的 id 或 class (.navbar)。这样就可以联系上可滚动区域。

注意可滚动项元素上的 id （<div id="section1">） 必须匹配导航栏上的链接选项 （<a href="#section1">)。

可选项data-offset 属性用于计算滚动位置时，距离顶部的偏移像素。 默认为 10 px。

设置相对定位: 使用 data-spy="scroll" 的元素需要将其 CSS position 属性设置为 "relative" 才能起作用。

以下实例设置了垂直滚动监听：


## 实例

```java
<body data-spy="scroll" data-target="#myScrollspy" data-offset="1">

  <div class="container-fluid">
    <div class="row">
      <nav class="col-sm-3 col-4" id="myScrollspy">
        <ul class="nav nav-pills flex-column">
          <li class="nav-item">
            <a class="nav-link active" href="#section1">Section 1</a>
          </li>
          ...
        </ul>
      </nav>
      <div class="col-sm-9 col-8">
        <div id="section1">
          <h1>Section 1</h1>
          <p>Try to scroll this page and look at the navigation list while scrolling!</p>
        </div>
        ...
      </div>
    </div>
  </div>

</body>
```


## 复习重点

- 能说明 `Bootstrap4 滚动监听` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
