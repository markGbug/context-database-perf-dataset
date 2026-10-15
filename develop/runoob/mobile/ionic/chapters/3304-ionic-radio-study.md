# Ionic：ionic 单选框

- 来源：[ionic 单选框](https://www.runoob.com/ionic/ionic-radio.html)
- 分类：移动开发
- 技术：Ionic
- 笔记类型：学习笔记
- 章节序号：3304

## 本章内容

ionic 单选按钮与标准 type="radio" 的 input元素类似。以下展示了现代app类型的单选按钮。

每个 item-radio 中的 type="radio" 的 input 元素的 name 属性都相同。radio-icon 类用于是否显示图标。

ionic 在单选项中使用了 <label> 元素，使其更易点击。


## 实例

```html
<div class="list">
<label class="item item-radio">
  <input type="radio" name="group" value="go" checked="checked">
   <div class="radio-content">
   <div class="item-content">
    Go
   </div>
   <i class="radio-icon ion-checkmark"></i>
  </div>
</label>

<label class="item item-radio">
  <input type="radio" name="group" value="python">
  <div class="radio-content">
   <div class="item-content">
    Python
   </div>
   <i class="radio-icon ion-checkmark"></i>
  </div>
</label>

<label class="item item-radio">
  <input type="radio" name="group" value="ruby">
  <div class="radio-content">
   <div class="item-content">
    Ruby
   </div>
   <i class="radio-icon ion-checkmark"></i>
  </div>
</label>

<label class="item item-radio">
  <input type="radio" name="group" value=".net">
  <div class="radio-content">
   <div class="item-content">
    .Net
   </div>
   <i class="radio-icon ion-checkmark"></i>
  </div>
</label>

<label class="item item-radio">
  <input type="radio" name="group" value="java">
  <div class="radio-content">
   <div class="item-content">
    Java
   </div>
   <i class="radio-icon ion-checkmark"></i>
  </div>
</label>

<label class="item item-radio">
  <input type="radio" name="group" value="php">
  <div class="radio-content">
   <div class="item-content">
    PHP
   </div>
   <i class="radio-icon ion-checkmark"></i>
  </div>
</label>
</div>
```

运行效果如下：


## 复习重点

- 能说明 `ionic 单选框` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
