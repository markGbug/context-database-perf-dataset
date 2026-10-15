# JavaScript：JavaScript HTML DOM 元素 (节点)

- 来源：[DOM 元素](https://www.runoob.com/js/js-htmldom-elements.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2810

## 本章内容

本章节介绍如何向文档中添加和移除元素(节点)。


## 创建新的 HTML 元素 (节点) - appendChild()

要创建新的 HTML 元素 (节点)需要先创建一个元素，然后在已存在的元素中添加它。


## 实例

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>

<script>
var para = document.createElement("p");
var node = document.createTextNode("这是一个新的段落。");
para.appendChild(node);

var element = document.getElementById("div1");
element.appendChild(para);
</script>
```


### 实例解析

以下代码是用于创建 <p> 元素:

```javascript
var para = document.createElement("p");
```

为 <p> 元素创建一个新的文本节点：

```javascript
var node = document.createTextNode("这是一个新的段落。");
```

将文本节点添加到 <p> 元素中：

```text
para.appendChild(node);
```

最后，在一个已存在的元素中添加 p 元素。

查找已存在的元素：

```javascript
var element = document.getElementById("div1");
```

添加到已存在的元素中:

```text
element.appendChild(para);
```


## 创建新的 HTML 元素 (节点) - insertBefore()

以上的实例我们使用了 appendChild() 方法，它用于添加新元素到尾部。

如果我们需要将新元素添加到开始位置，可以使用 insertBefore() 方法:


## 实例

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>

<script>
var para = document.createElement("p");
var node = document.createTextNode("这是一个新的段落。");
para.appendChild(node);

var element = document.getElementById("div1");
var child = document.getElementById("p1");
element.insertBefore(para, child);
</script>
```


## 移除已存在的元素

要移除一个元素，你需要知道该元素的父元素。


## 实例

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>

<script>
var parent = document.getElementById("div1");
var child = document.getElementById("p1");
parent.removeChild(child);
</script>
```

注意：早期的 Internet Explorer 浏览器不支持 node.remove() 方法。


### 实例解析

HTML 文档中 <div> 元素包含两个子节点 (两个 <p> 元素):

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>
```

查找 id="div1" 的元素:

```javascript
var parent = document.getElementById("div1");
```

查找 id="p1" 的 <p> 元素:

```javascript
var child = document.getElementById("p1");
```

从父元素中移除子节点：

```text
parent.removeChild(child);
```

以下代码是已知要查找的子元素，然后查找其父元素，再删除这个子元素（删除节点必须知道父节点）：

```javascript
var child = document.getElementById("p1");
child.parentNode.removeChild(child);
```


## 替换 HTML 元素 - replaceChild()

我们可以使用 replaceChild() 方法来替换 HTML DOM 中的元素。


## 实例

```html
<div id="div1">
<p id="p1">这是一个段落。</p>
<p id="p2">这是另外一个段落。</p>
</div>

<script>
var para = document.createElement("p");
var node = document.createTextNode("这是一个新的段落。");
para.appendChild(node);

var parent = document.getElementById("div1");
var child = document.getElementById("p1");
parent.replaceChild(para, child);
</script>
```


## HTML DOM 教程

在我们的 JavaScript 教程的 HTML DOM 部分，您已经学到了：

- 如何改变 HTML 元素的内容 (innerHTML)
- 如何改变 HTML 元素的样式 (CSS)
- 如何对 HTML DOM 事件作出反应
- 如何添加或删除 HTML 元素

如果您希望学到更多有关使用 JavaScript 访问 HTML DOM 的知识，请访问我们完整的 HTML DOM 教程。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM 元素` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
