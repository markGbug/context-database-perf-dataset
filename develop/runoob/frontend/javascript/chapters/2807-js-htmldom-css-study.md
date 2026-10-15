# JavaScript：JavaScript HTML DOM - 改变CSS

- 来源：[DOM CSS](https://www.runoob.com/js/js-htmldom-css.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2807

## 本章内容

HTML DOM 允许 JavaScript 改变 HTML 元素的样式。


## 改变 HTML 样式

如需改变 HTML 元素的样式，请使用这个语法：

下面的例子会改变 <p> 元素的样式：


## 实例

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p id="p1">Hello World!</p>
<p id="p2">Hello World!</p>
<script>
document.getElementById("p2").style.color="blue";
document.getElementById("p2").style.fontFamily="Arial";
document.getElementById("p2").style.fontSize="larger";
</script>
<p>以上段落通过脚本修改。</p>

</body>
</html>
```


## 使用事件

HTML DOM 允许我们通过触发事件来执行代码。

比如以下事件：

- 元素被点击。
- 页面加载完成。
- 输入框被修改。
- ……

在接下来的章节，你会学到更多关于事件的知识。

本例改变了 id="id1" 的 HTML 元素的样式，当用户点击按钮时：


## 实例


## 更多实例

Visibility 如何使元素不可见。您希望元素显示或消失吗？


## 复习重点

- 能说明 `DOM CSS` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
