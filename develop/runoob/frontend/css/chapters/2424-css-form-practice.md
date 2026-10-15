# CSS：CSS 表单

- 来源：[CSS 表单](https://www.runoob.com/css/css-form.html)
- 分类：前端开发
- 技术：CSS
- 笔记类型：练习笔记
- 章节序号：2424

## 本章内容

一个表单案例，我们使用 CSS 来渲染 HTML 的表单元素：


## CSS 实例

```text
input[type=text], select {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

input[type=submit] {
  width: 100%;
  background-color: #4CAF50;
  color: white;
  padding: 14px 20px;
  margin: 8px 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

input[type=submit]:hover {
  background-color: #45a049;
}

div {
  border-radius: 5px;
  background-color: #f2f2f2;
  padding: 20px;
}
```


## 输入框(input) 样式

使用 width 属性来设置输入框的宽度：


## CSS 实例

```text
input {
  width: 100%;
}
```

以上实例中设置了所有 <input> 元素的宽度为 100%，如果你只想设置指定类型的输入框可以使用以下属性选择器：

- input[type=text] - 选取文本输入框
- input[type=password] - 选择密码的输入框
- input[type=number] - 选择数字的输入框
- ...


## 输入框填充

使用 padding 属性可以在输入框中添加内边距。


## CSS 实例

```text
input[type=text] {
  width: 100%;
  padding: 12px 20px;
  margin: 8px 0;
  box-sizing: border-box;
}
```

注意我们设置了 box-sizing 属性为 border-box。这样可以确保浏览器呈现出带有指定宽度和高度的输入框是把边框和内边距一起计算进去的。 更多内容可以阅读 CSS3 框大小 。


## 输入框(input) 边框

使用 border 属性可以修改 input 边框的大小或颜色，使用 border-radius 属性可以给 input 添加圆角：


## CSS 实例

```text
input[type=text] {
  border: 2px solid red;
  border-radius: 4px;
}
```

如果你只想添加底部边框可以使用 border-bottom 属性:


## CSS 实例

```text
input[type=text] {
  border: none;
  border-bottom: 2px solid red;
}
```


## 输入框(input) 颜色

可以使用 background-color 属性来设置输入框的背景颜色，color 属性用于修改文本颜色：


## CSS 实例

```text
input[type=text] {
  background-color: #3CBC8D;
  color: white;
}
```


## 输入框(input) 聚焦

默认情况下，一些浏览器在输入框获取焦点时（点击输入框）会有一个蓝色轮廓。我们可以设置 input 样式为 outline: none; 来忽略该效果。

使用 :focus 选择器可以设置输入框在获取焦点时的样式：


## CSS 实例

```text
input[type=text]:focus {
  background-color: lightblue;
}
```


## CSS 实例

```text
input[type=text]:focus {
  border: 3px solid #555;
}
```


## 输入框(input) 图标

如果你想在输入框中添加图标，可以使用 background-image 属性和用于定位的background-position 属性。注意设置图标的左边距，让图标有一定的空间：


## CSS 实例

```text
input[type=text] {
  background-color: white;
  background-image: url('searchicon.png');
  background-position: 10px 10px;
  background-repeat: no-repeat;
  padding-left: 40px;
}
```


## 带动画的搜索框

以下实例使用了 CSS transition 属性，该属性设置了输入框在获取焦点时会向右延展。你可以在 CSS 动画 章节查看更多内容。


## CSS 实例

```text
input[type=text] {
  -webkit-transition: width 0.4s ease-in-out;
  transition: width 0.4s ease-in-out;
}

input[type=text]:focus {
  width: 100%;
}
```


## 文本框（textarea）样式

注意: 使用 resize 属性来禁用文本框可以重置大小的功能（一般拖动右下角可以重置大小）。


## CSS 实例

```text
textarea {
  width: 100%;
  height: 150px;
  padding: 12px 20px;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
  background-color: #f8f8f8;
  resize: none;
}
```


## 下拉菜单（select）样式


## CSS 实例

```text
select {
  width: 100%;
  padding: 16px 20px;
  border: none;
  border-radius: 4px;
  background-color: #f1f1f1;
}
```


## 按钮样式


## CSS 实例

```text
input[type=button], input[type=submit], input[type=reset] {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 16px 32px;
  text-decoration: none;
  margin: 4px 2px;
  cursor: pointer;
}

/* 提示: 使用 width: 100% 设置全宽按钮 */
```

更多内容可以参考我们的 CSS 按钮 教程。


## 响应式表单

响应式表单可以根据浏览器窗口的大小重新布局各个元素，我们可以通过重置浏览器窗口大小来查看效果：

高级: 以下实例使用了CSS3 多媒体查询 来创建一个响应式表单。


## 后续章节

- CSS 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `CSS 表单` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
