# Bootstrap5：Bootstrap5 下拉菜单

- 来源：[Bootstrap5 下拉菜单](https://www.runoob.com/bootstrap5/bootstrap5-form-select.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：学习笔记
- 章节序号：2371

## 本章内容

下拉菜单可以是单选下拉菜单，也可以是多选的下拉菜单。

单选下拉菜单：

多选下拉菜单：

在 Bootstrap5 中下拉菜单 <select> 元素可以使用 .form-select 类来渲染 :


## 实例

```html
<select class="form-select">
  <option>1</option>
  <option>2</option>
  <option>3</option>
  <option>4</option>
</select>
```

下拉菜单通过 .form-select-lg 或 .form-select-sm 类来修改大小：


## 实例

```html
<select class="form-select form-select-lg">
<select class="form-select">
<select class="form-select form-select-sm">
```

效果如下图：

disabled 属性可以禁止下拉菜单被选择：


## 实例

```html
<select class="form-select" disabled>
  <option>1</option>
  <option>2</option>
  <option>3</option>
  <option>4</option>
</select>
```


## 数据列表

Bootstrap 也可以通过 datalist 标签为 <input> 元素设置下拉菜单：

以下实例从列表中选择一个网站：


## 实例

```html
<label for="browser" class="form-label">选择你喜欢的网站：</label>
<input class="form-control" list="sites" name="site" id="site">
<datalist id="sites">
  <option value="Google">
  <option value="Runoob">
  <option value="Taobao">
  <option value="Wiki">
  <option value="Zhihu">
</datalist>
```

效果如下图：


## 复习重点

- 能说明 `Bootstrap5 下拉菜单` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
