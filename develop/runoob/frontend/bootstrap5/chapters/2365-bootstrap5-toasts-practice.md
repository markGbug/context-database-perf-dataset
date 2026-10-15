# Bootstrap5：Bootstrap5 消息弹窗(Toasts)

- 来源：[Bootstrap5 消息弹窗](https://www.runoob.com/bootstrap5/bootstrap5-toasts.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：练习笔记
- 章节序号：2365

## 本章内容

Bootstrap5 弹窗 (Toasts) 是一种轻量级的通知组件，用于在页面的角落或底部显示临时性的信息、通知或警告。

弹窗通常用于向用户显示短期消息，比如成功消息、错误消息、警告或其他通知。

弹窗可以在页面的不同位置显示，包括左上角、右上角、左下角、右下角以及页面底部中央。


### 如何创建弹窗

要创建弹窗可以使用 .toast 类，并在该类里添加 .toast-header 和 .toast-body 类来表示标题和内容。

注意：弹窗默认是关闭的，可以使用 .show 来设置显示，关闭弹窗可以在 <button>元素上添加 data-bs-dismiss="toast":


## 实例

```html
<div class="toast show">
  <div class="toast-header">
    弹窗标题
    <button type="button" class="btn-close" data-bs-dismiss="toast"></button>
  </div>
  <div class="toast-body">
    这是一个Bootstrap 5弹窗示例。
  </div>
</div>
```

要通过点击按钮显示弹窗，您需要使用 JavaScript 对其进行初始化：通过 ID 获取指定元素的点击事件并调用 toast() 方法。

当点击按钮时，以下代码将显示页面中的所有 toast 类：


## 实例

```javascript
document.getElementById("toastbtn").onclick = function() {
  var toastElList = [].slice.call(document.querySelectorAll('.toast'))
  var toastList = toastElList.map(function(toastEl) {
    return new bootstrap.Toast(toastEl)
  })
  toastList.forEach(toast => toast.show())
}
```

将弹窗显示在右下角：


## 实例

```html
<div class="container mt-5">
    <button class="btn btn-primary" onclick="showToast()">显示弹窗</button>
</div>

<div class="position-fixed bottom-0 end-0 p-3">
    <div id="toast" class="toast" role="alert" aria-live="assertive" aria-atomic="true">
        <div class="toast-header">
            <strong class="me-auto">Bootstrap Toast</strong>
            <button type="button" class="btn-close" data-bs-dismiss="toast" aria-label="Close"></button>
        </div>
        <div class="toast-body">
            这是一个Bootstrap 5弹窗示例。
        </div>
    </div>
</div>
```


## 实例

```html
<!--显示多个弹窗 -->

<div aria-live="polite" aria-atomic="true" class="position-relative">
    <!-- Position it: -->
    <!-- - `.toast-container` 设置弹窗直接的空隙 -->
    <!-- - `top-0` & `end-0` 设置弹窗显示位置-->
    <!-- - `.p-3` 设置外边距  -->
    <div class="toast-container top-0 end-0 p-3">

    <!-- 这里设置多个弹窗代码 -->
    <div class="toast fade show" role="alert" aria-live="assertive" aria-atomic="true">
        <div class="toast-header">
        <svg class="bd-placeholder-img rounded me-2" width="20" height="20" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" preserveAspectRatio="xMidYMid slice" focusable="false"><rect width="100%" height="100%" fill="#007aff"></rect></svg>
        <strong class="me-auto">弹窗实例</strong>
        <small class="text-muted">刚刚</small>
        <button type="button" class="btn-close" data-bs-dismiss="toast" aria-label="Close"></button>
        </div>
        <div class="toast-body">
        这是第二个消息
        </div>
    </div>

    <div class="toast fade show" role="alert" aria-live="assertive" aria-atomic="true">
        <div class="toast-header">
        <svg class="bd-placeholder-img rounded me-2" width="20" height="20" xmlns="http://www.w3.org/2000/svg" aria-hidden="true" preserveAspectRatio="xMidYMid slice" focusable="false"><rect width="100%" height="100%" fill="#007aff"></rect></svg>
        <strong class="me-auto">弹窗实例</strong>
        <small class="text-muted">2 秒前</small>
        <button type="button" class="btn-close" data-bs-dismiss="toast" aria-label="Close"></button>
        </div>
        <div class="toast-body">
        这是第一个消息
        </div>
    </div>
    </div>
</div>

<!-- 显示多个弹窗 结束 -->
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap5 消息弹窗` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
