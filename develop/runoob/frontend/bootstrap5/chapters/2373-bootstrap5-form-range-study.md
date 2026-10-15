# Bootstrap5：Bootstrap5 选择区间

- 来源：[Bootstrap5 选择区间](https://www.runoob.com/bootstrap5/bootstrap5-form-range.html)
- 分类：前端开发
- 技术：Bootstrap5
- 笔记类型：学习笔记
- 章节序号：2373

## 本章内容

要设置一个选择区间可以在 input 元素中添加 type="range" 并使用 .form-range 类：

选择区间：


## 实例

```html
<label for="customRange" class="form-label">Custom range</label>
<input type="range" class="form-range" id="customRange">
```


## 步长

默认情况下，步长为 1，可以通过 step 属性来设置：


## 实例

```html
<input type="range" class="form-range" step="10">
```


## 最大最小值

默认情况下，最小值为 0，最大值为 100，可以通过 min（最小） 或 max（最大） 属性来设置：


## 实例

```html
<input type="range" class="form-range" min="0" max="4">
```


## 复习重点

- 能说明 `Bootstrap5 选择区间` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
