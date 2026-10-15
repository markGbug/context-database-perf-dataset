# Bootstrap5：Bootstrap5 复选框与单选框

- 来源：[Bootstrap5 复选框与单选框](https://www.runoob.com/bootstrap5/bootstrap5-form-check-radio.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：练习笔记
- 章节序号：2372

## 本章内容

如果您希望用户从预设选项列表中选择任意数量的选项，可以使用复选框：


## 实例

```html
<div class="form-check">
  <input class="form-check-input" type="checkbox" id="check1" name="option1" value="something" checked>
  <label class="form-check-label">Option 1</label>
</div>
```

复选框通过使用 class="form-check" 来确保标签和复选框有适当边距。

.form-check-label 类添加到标签元素，.form-check 容器内添加 .form-check-input 类来设置复选框的样式。

checked 属性用于设置默认选中的选项。


## 单选框

如果您希望用户从预设选项列表中选择一个选项，可以使用单选框：


## 实例

```html
<div class="form-check">
  <input type="radio" class="form-check-input" id="radio1" name="optradio" value="option1" checked>Option 1
  <label class="form-check-label" for="radio1"></label>
</div>
<div class="form-check">
  <input type="radio" class="form-check-input" id="radio2" name="optradio" value="option2">Option 2
  <label class="form-check-label" for="radio2"></label>
</div>
<div class="form-check">
  <input type="radio" class="form-check-input" disabled>Option 3
  <label class="form-check-label"></label>
</div>
```


## 切换开关

如果你想把复选框变成一个可切换的开关，可以在 .form-check 容器内使用 .form-switch 类:


## 实例

```html
<div class="form-check form-switch">
  <input class="form-check-input" type="checkbox" id="mySwitch" name="darkmode" value="yes" checked>
  <label class="form-check-label" for="mySwitch">Dark Mode</label>
</div>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap5 复选框与单选框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
