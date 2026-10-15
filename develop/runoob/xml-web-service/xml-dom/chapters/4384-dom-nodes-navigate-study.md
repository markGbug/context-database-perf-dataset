# XML DOM：XML DOM - 导航节点

- 来源：[DOM 导航](https://www.runoob.com/dom/dom-nodes-navigate.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4384

## 本章内容

可通过使用节点间的关系对节点进行导航。


## 导航 DOM 节点

通过节点间的关系访问节点树中的节点，通常称为导航节点（"navigating nodes"）。

在 XML DOM 中，节点的关系被定义为节点的属性：

- parentNode
- childNodes
- firstChild
- lastChild
- nextSibling
- previousSibling

下面的图像展示了 books.xml 中节点树的一个部分，并说明了节点之间的关系：


## DOM - 父节点

所有的节点都仅有一个父节点。下面的代码导航到 <book> 的父节点：


## 实例

```text
xmlDoc=loadXMLDoc("books.xml");

x=xmlDoc.getElementsByTagName("book")[0];
document.write(x.parentNode.nodeName);
```

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取第一个 <book> 元素
- 输出 "x" 的父节点的节点名称


## 避免空的文本节点

Firefox 以及其他一些浏览器，把空的空白或换行当作文本节点，而 Internet Explorer 不会这么做。

这会在使用以下属性：firstChild、lastChild、nextSibling、previousSibling 时产生一个问题。

为了避免导航到空的文本节点（元素节点之间的空格和换行符），我们使用一个函数来检查节点类型：

```java
function get_nextSibling(n)
{
  y=n.nextSibling;
  while (y.nodeType!=1)
  {
    y=y.nextSibling;
  }
  return y;
}
```

上面的函数允许您使用 get_nextSibling（node）来代替 node.nextSibling 属性。

代码解释：

元素节点的类型是 1。如果同级节点不是元素节点，就移动到下一个节点，直到找到元素节点为止。通过这个办法，在 Internet Explorer 和 Firefox 中，都可以得到相同的结果。


## 获取第一个子元素

下面的代码显示第一个 <book> 的第一个元素：


## 实例

```html
<html>
<head>
<script src="loadxmldoc.js">
</script>
<script>
```

```java
// 检测第一个节点是否为元素节点
function get_firstChild(n)
{
  y=n.firstChild;
  while (y.nodeType!=1)
  {
    y=y.nextSibling;
  }
  return y;
}
</script>
</head>

<body>
<script>
xmlDoc=loadXMLDoc("books.xml");

x=get_firstChild(xmlDoc.getElementsByTagName("book")[0]);
document.write(x.nodeName);
```

```text
</script>
</body>
</html>
```

输出：

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 在第一个 <book> 元素上使用 get_firstChild 函数，来获取第一个子节点（属于元素节点）
- 输出第一个子节点（属于元素节点）的节点名称


## 更多实例

lastChild() 本例使用 lastChild() 方法和一个自定义函数来获取节点的最后一个子节点

nextSibling() 本例使用 nextSibling() 方法和一个自定义函数来获取节点的下一个同级节点

previousSibling() 本例使用 previousSibling() 方法和一个自定义函数来获取节点的上一个同级节点


## 复习重点

- 能说明 `DOM 导航` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
