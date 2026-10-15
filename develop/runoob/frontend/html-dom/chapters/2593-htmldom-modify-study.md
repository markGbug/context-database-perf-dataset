# HTML DOM：HTML DOM - 修改

- 来源：[HTML DOM 修改](https://www.runoob.com/htmldom/htmldom-modify.html)
- 分类：前端开发
- 技术：HTML DOM
- 笔记类型：学习笔记
- 章节序号：2593

## 本章内容

修改 HTML = 改变元素、属性、样式和事件。


## 修改 HTML 元素

修改 HTML DOM 意味着许多不同的方面：

- 改变 HTML 内容
- 改变 CSS 样式
- 改变 HTML 属性
- 创建新的 HTML 元素
- 删除已有的 HTML 元素
- 改变事件（处理程序）

在接下来的章节，我们会深入学习修改 HTML DOM 的常用方法。


## 创建 HTML 内容

改变元素内容的最简单的方法是使用 innerHTML 属性。

下面的例子改变一个 <p> 元素的 HTML 内容：


## 实例

```html
<p id="p1">Hello World!</p>

<script>
document.getElementById("p1").innerHTML="新文本!";
</script>

<p>段落通过脚本来修改内容。</p>
```


## 改变 HTML 样式

通过 HTML DOM，您能够访问 HTML 元素的样式对象。

下面的例子改变一个段落的 HTML 样式：


## 实例

```html
<p id="p1">Hello world!</p>
<p id="p2">Hello world!</p>

<script>
document.getElementById("p2").style.color="blue";
document.getElementById("p2").style.fontFamily="Arial";
document.getElementById("p2").style.fontSize="larger";
</script>
```


## 创建新的 HTML 元素

如需向 HTML DOM 添加新元素，您首先必须创建该元素（元素节点），然后把它追加到已有的元素上。


## 实例

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另一个段落。</p>
</div>
<script>
var para=document.createElement("p");
var node=document.createTextNode("这是一个新段落。");
para.appendChild(node);
var element=document.getElementById("div1");
element.appendChild(para);
</script>
```


## 复习重点

- 能说明 `HTML DOM 修改` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
