# Bootstrap5：Bootstrap5 表单浮动标签

- 来源：[Bootstrap5 表单浮动标签](https://www.runoob.com/bootstrap5/bootstrap5-form-floating-labels.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：学习笔记
- 章节序号：2375

## 本章内容

默认情况下，标签内容一般显示在 input 输入框的上方：


## Bootstrap 实例

```html
<div class="form-floating mb-3 mt-3">
  <input type="text" class="form-control" id="email" placeholder="Enter email" name="email">
  <label for="email">Email</label>
</div>

<div class="form-floating mt-3 mb-3">
  <input type="text" class="form-control" id="pwd" placeholder="Enter password" name="pswd">
  <label for="pwd">Password</label>
</div>
```

注意事项： <label> 元素必须在 <input> 元素之后，并且每个 <input> 元素都需要 placeholder 属性。


## 文本框

文本框 textarea 也可以有浮动效果：


## Bootstrap 实例

```html
<div class="form-floating">
  <textarea class="form-control" id="comment" name="text" placeholder="Comment goes here"></textarea>
  <label for="comment">Comments</label>
</div>
```


## 选择框

我们可以在选择菜单上使用浮动标签，它将始终显示在选择菜单的左上角，不会有点击浮动效果：


## Bootstrap 实例

```html
<div class="form-floating">
  <select class="form-select" id="sel1" name="sellist">
    <option>1</option>
    <option>2</option>
    <option>3</option>
    <option>4</option>
  </select>
  <label for="sel1" class="form-label">Select list (select one):</label>
</div>
```


## 复习重点

- 能说明 `Bootstrap5 表单浮动标签` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
