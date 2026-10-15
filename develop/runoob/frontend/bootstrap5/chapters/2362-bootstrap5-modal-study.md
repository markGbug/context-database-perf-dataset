# Bootstrap5：Bootstrap5 模态框

- 来源：[Bootstrap5 模态框](https://www.runoob.com/bootstrap5/bootstrap5-modal.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：学习笔记
- 章节序号：2362

## 本章内容

模态框（Modal）是覆盖在父窗体上的子窗体。通常，目的是显示来自一个单独的源的内容，可以在不离开父窗体的情况下有一些互动。子窗体可提供信息交互等。


## 如何创建模态框

以下实例创建了一个简单的模态框效果 ：


## 实例

```html
<button type="button" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#myModal">
  打开模态框
</button>


<!-- 模态框 -->
<div class="modal" id="myModal">
  <div class="modal-dialog">
    <div class="modal-content">

      <!-- 模态框头部 -->
      <div class="modal-header">
        <h4 class="modal-title">模态框标题</h4>
        <button type="button" class="btn-close" data-bs-dismiss="modal"></button>
      </div>

      <!-- 模态框内容 -->
      <div class="modal-body">
        模态框内容..
      </div>

      <!-- 模态框底部 -->
      <div class="modal-footer">
        <button type="button" class="btn btn-danger" data-bs-dismiss="modal">关闭</button>
      </div>

    </div>
  </div>
</div>
```


## 添加动画

使用 .fade 类可以设置模态框弹出或关闭的效果:


## 实例

```html
<!-- 添加动画效果 -->
<div class="modal fade"></div>

<!-- 不使用动画效果 -->
<div class="modal"></div>
```


## 模态框尺寸

我们可以通过添加 .modal-sm 类来创建一个小模态框，.modal-lg 类可以创建一个大模态框。

尺寸类放在 <div>元素的 .modal-dialog 类后 :


## 实例 - 小模态框

```html
<div class="modal-dialog modal-sm">
```


## 实例 - 大模态框

```html
<div class="modal-dialog modal-lg">
```


## 实例 - 超大模态框

```html
<div class="modal-dialog modal-xl">
```


### 全屏幕显示

使用 .modal-fullscreen 类可以让模态框全屏幕显示:


## 实例 - 全屏幕显示

```html
<div class="modal-dialog modal-fullscreen">
```

使用 .modal-fullscreen-*-* 类可以控制在什么尺寸下全屏幕显示:


## 模态框居中显示

使用 .modal-dialog-centered 类可以设置模态框水平和垂直方向都居中显示:


## 实例

```html
<div class="modal-dialog modal-dialog-centered">
```


## 模态框滚动条

默认情况下模态框如果包含很多内容，页面会自动生成一个滚动，模态框随着页面的滚动而滚动:


## 实例

```html
<div class="modal-dialog">
```

如果我们只想在模态框里头设置一个滚动条，可以使用 .modal-dialog-scrollable 类：


## 实例

```html
<div class="modal-dialog modal-dialog-scrollable">
```


## 复习重点

- 能说明 `Bootstrap5 模态框` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
