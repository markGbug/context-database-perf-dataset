# Bootstrap4：Bootstrap4 模态框

- 来源：[Bootstrap4 模态框](https://www.runoob.com/bootstrap4/bootstrap4-modal.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：学习笔记
- 章节序号：2331

## 本章内容

模态框（Modal）是覆盖在父窗体上的子窗体。通常，目的是显示来自一个单独的源的内容，可以在不离开父窗体的情况下有一些互动。子窗体可提供信息交互等。


## 如何创建模态框

以下实例创建了一个简单的模态框效果 ：


## 实例

```html
<!-- 按钮：用于打开模态框 -->
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#myModal">
  打开模态框
</button>

<!-- 模态框 -->
<div class="modal fade" id="myModal">
  <div class="modal-dialog">
    <div class="modal-content">

      <!-- 模态框头部 -->
      <div class="modal-header">
        <h4 class="modal-title">模态框头部</h4>
        <button type="button" class="close" data-dismiss="modal">×</button>
      </div>

      <!-- 模态框主体 -->
      <div class="modal-body">
        模态框内容..
      </div>

      <!-- 模态框底部 -->
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">关闭</button>
      </div>

    </div>
  </div>
</div>
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


## 复习重点

- 能说明 `Bootstrap4 模态框` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
