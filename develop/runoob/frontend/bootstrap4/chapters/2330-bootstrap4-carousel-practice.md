# Bootstrap4：Bootstrap4 轮播

- 来源：[Bootstrap4 轮播](https://www.runoob.com/bootstrap4/bootstrap4-carousel.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：练习笔记
- 章节序号：2330

## 本章内容

轮播是一个循环的幻灯片：


## 如何创建轮播

以下实例创建了一个简单的图片轮播效果 ：


## 实例

```html
<div id="demo" class="carousel slide" data-ride="carousel">

  <!-- 指示符 -->
  <ul class="carousel-indicators">
    <li data-target="#demo" data-slide-to="0" class="active"></li>
    <li data-target="#demo" data-slide-to="1"></li>
    <li data-target="#demo" data-slide-to="2"></li>
  </ul>

  <!-- 轮播图片 -->
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img src="https://static.jyshare.com/images/mix/img_fjords_wide.jpg">
    </div>
    <div class="carousel-item">
      <img src="https://static.jyshare.com/images/mix/img_nature_wide.jpg">
    </div>
    <div class="carousel-item">
      <img src="https://static.jyshare.com/images/mix/img_mountains_wide.jpg">
    </div>
  </div>

  <!-- 左右切换按钮 -->
  <a class="carousel-control-prev" href="#demo" data-slide="prev">
    <span class="carousel-control-prev-icon"></span>
  </a>
  <a class="carousel-control-next" href="#demo" data-slide="next">
    <span class="carousel-control-next-icon"></span>
  </a>

</div>
```


## 轮播图片上添加描述

在每个 <div class="carousel-item"> 内添加 <div class="carousel-caption"> 来设置轮播图片的描述文本：:


## 实例

```html
<div class="carousel-item">
  <img src="https://static.jyshare.com/images/mix/img_fjords_wide.jpg">
  <div class="carousel-caption">
    <h3>第一张图片描述标题</h3>
    <p>描述文字!</p>
  </div>
</div>
```


### 以上实例中使用的类说明


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap4 轮播` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
