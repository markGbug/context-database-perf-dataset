# HTML DOM：HTML DOM - 元素

- 来源：[HTML DOM 元素](https://www.runoob.com/htmldom/htmldom-elements.html)
- 分类：前端开发
- 技术：HTML DOM
- 笔记类型：学习笔记
- 章节序号：2595

## 本章内容

添加、删除和替换 HTML 元素。


## 创建新的 HTML 元素 - createElement()

如需向 HTML DOM 添加新元素，您首先必须创建该元素，然后把它追加到已有的元素上。


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


## 实例解析

这段代码创建了一个新的 <p> 元素：

如需向 <p> 元素添加文本，您首先必须创建文本节点。这段代码创建文本节点：

然后您必须向 <p> 元素追加文本节点：

最后，您必须向已有元素追加这个新元素。

这段代码查找到一个已有的元素：

这段代码向这个已存在的元素追加新元素：


## 创建新的 HTML 元素 - insertBefore()

上一个例子中的 appendChild() 方法，将新元素作为父元素的最后一个子元素进行添加。

如果不希望如此，您可以使用 insertBefore() 方法：


## 实例

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>

<script>
var para=document.createElement("p");
var node=document.createTextNode("这是一个新段落。");
para.appendChild(node);

var element=document.getElementById("div1");
var child=document.getElementById("p1");
element.insertBefore(para,child);
</script>
```


## 删除已有的 HTML 元素

如需删除 HTML 元素，您必须清楚该元素的父元素：


## 实例

```html
<div id="div1">
    <p id="p1">这是一个段落。</p>
    <p id="p2">这是另一个段落。</p>
</div>
<script>
var parent=document.getElementById("div1");
var child=document.getElementById("p1");
parent.removeChild(child);
</script>
```


## 实例解析

这个 HTML 文档包含一个带有两个子节点（两个 <p> 元素）的 <div> 元素：

查找 id="div1" 的元素：

查找 id="p1" 的 <p> 元素：

从父元素中删除子元素：

这里提供一个常用的解决方法：找到您需要删除的子元素，然后使用 parentNode 属性来查找其父元素：


## 替换 HTML 元素

如需替换 HTML DOM 中的元素，请使用 replaceChild() 方法：


## 实例

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>

<script>
var parent=document.getElementById("div1");
var child=document.getElementById("p1");
var para=document.createElement("p");
var node=document.createTextNode("这是一个新的段落。");
para.appendChild(node);
parent.replaceChild(para,child);
</script>
```


## 复习重点

- 能说明 `HTML DOM 元素` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
