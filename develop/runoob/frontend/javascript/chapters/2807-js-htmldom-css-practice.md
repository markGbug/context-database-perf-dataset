# JavaScript：JavaScript HTML DOM - 改变CSS

- 来源：[DOM CSS](https://www.runoob.com/js/js-htmldom-css.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
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


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM CSS` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
