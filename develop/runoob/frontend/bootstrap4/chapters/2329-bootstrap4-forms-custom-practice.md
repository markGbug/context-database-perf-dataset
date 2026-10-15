# Bootstrap4：Bootstrap4 自定义表单

- 来源：[Bootstrap4 自定义表单](https://www.runoob.com/bootstrap4/bootstrap4-forms-custom.html)
- 分类：前端开发
- 技术：Bootstrap4
- 笔记类型：练习笔记
- 章节序号：2329

## 本章内容

## 自定义复选框

如果要自定义一个复选框，可以设置 <div> 为父元素，类为 .custom-control 和 .custom-checkbox，复选框作为子元素放在该 <div> 里头，然后复选框设置为 type="checkbox"，类为 .custom-control-input。

复选框的文本使用 label 标签，标签使用 .custom-control-label 类，label 的 for 属性值需要匹配复选框的 id。


## Bootstrap4 实例

```html
<form>
  <div class="custom-control custom-checkbox">
    <input type="checkbox" class="custom-control-input" id="customCheck" name="example1">
    <label class="custom-control-label" for="customCheck">自定义复选框</label>
  </div>
</form>
```


## 自定义单选框

如果要自定义一个单选框，可以设置 <div> 为父元素，类为 .custom-control 和 .custom-radio，单选框作为子元素放在该 <div> 里头，然后单选框设置为 type="radio"，类为 .custom-control-input。

单选框的文本使用 label 标签，标签使用 .custom-control-label 类，label 的 for 属性值需要匹配单选框的 id。


## Bootstrap4 实例

```html
<form>
  <div class="custom-control custom-radio">
    <input type="radio" class="custom-control-input" id="customRadio" name="example1" value="customEx">
    <label class="custom-control-label" for="customRadio">自定义单选框</label>
  </div>
</form>
```


## 自定义控件显示在同一行

我们可以在外部元素上使用 .custom-control-inline 类来包裹自定义表单控件，这样自定义表单控件就能显示在同一行：


## Bootstrap4 实例

```html
<form>
  <div class="custom-control custom-radio custom-control-inline">
    <input type="radio" class="custom-control-input" id="customRadio" name="example" value="customEx">
    <label class="custom-control-label" for="customRadio">自定义单选框 1</label>
  </div>
  <div class="custom-control custom-radio custom-control-inline">
    <input type="radio" class="custom-control-input" id="customRadio2" name="example" value="customEx">
    <label class="custom-control-label" for="customRadio2">自定义单选框 2</label>
  </div>
</form>
```


## 自定义选择菜单

创建自定义选择菜单可以在 <select> 元素上添加 .custom-select 类:


## Bootstrap4 实例

```html
<form>
  <select name="cars" class="custom-select-sm">
    <option selected>自定义选择菜单</option>
    <option value="Google">Google</option>
    <option value="Runoob">Runoob</option>
    <option value="Taobao">Taobao</option>
  </select>
</form>
```

如果我们要设置自定义选择菜单大小，可以使用 .custom-select-sm、.custom-select-lg 来设置它们的大小:


## Bootstrap4 实例

```html
<form>
  <!-- 小 -->
  <select name="cars" class="custom-select-sm">
    <option selected>比较小的自定义选择菜单</option>
    <option value="Google">Google</option>
    <option value="Runoob">Runoob</option>
    <option value="Taobao">Taobao</option>
  </select>

  <!-- 大 -->
  <select name="cars" class="custom-select-lg">
    <option selected>比较大的自定义选择菜单</option>
    <option value="Google">Google</option>
    <option value="Runoob">Runoob</option>
    <option value="Taobao">Taobao</option>
  </select>
</form>
```


## 自定义滑块控件

我们可以在 input 为 type="range" 的输入框中添加 .custom-range 类来设置自定义滑块控件:


## Bootstrap4 实例

```html
<form>
  <label for="customRange">自定义滑块控件</label>
  <input type="range" class="custom-range" id="customRange" name="points1">
</form>
```


## 自定义文件上传控件

我们可以在父元素添加 .custom-file 类，然后在 input 设置为 type="file" 并添加 .custom-file-input:

上传控件的文本使用 label 标签，标签使用 .custom-file-label 类，label 的 for 属性值需要匹配上传控件 id。


## Bootstrap4 实例

```html
<form>
  <div class="custom-file">
    <input type="file" class="custom-file-input" id="customFile">
    <label class="custom-file-label" for="customFile">选择文件</label>
  </div>
</form>
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Bootstrap4 自定义表单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
