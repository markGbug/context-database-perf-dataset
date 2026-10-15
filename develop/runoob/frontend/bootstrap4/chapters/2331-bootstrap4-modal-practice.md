# Bootstrap4：Bootstrap4 模态框

- 来源：[Bootstrap4 模态框](https://www.runoob.com/bootstrap4/bootstrap4-modal.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap4 模态框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
