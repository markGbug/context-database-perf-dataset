# XML DOM：XML DOM 删除节点

- 来源：[DOM 删除节点](https://www.runoob.com/dom/dom-nodes-remove.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：练习笔记
- 章节序号：4387

## 本章内容

removeChild() 方法删除指定节点。

removeAttribute() 方法删除指定属性。


## 尝试一下 - 实例

下面的实例使用 XML 文件 books.xml。 函数 loadXMLDoc()，位于外部 JavaScript 中，用于加载 XML 文件。

删除元素节点 本例使用 removeChild() 来删除第一个 <book> 元素。

删除当前元素节点 本例使用 parentNode 和 removeChild() 来删除当前的 <book> 元素。

删除文本节点 本例使用 removeChild() 来删除第一个 <title> 元素的文本节点。

清空文本节点的文本 本例使用 nodeValue() 属性来清空第一个 <title> 元素的文本节点。

根据名称删除属性 本例使用 removeAttribute() 从第一个 <book> 元素中删除 "category" 属性。

根据对象删除属性 本例使用 removeAttributeNode() 从所有 <book> 元素中删除所有属性。


## 删除元素节点

removeChild() 方法删除指定的节点。

当一个节点被删除时，其所有子节点也会被删除。

下面的代码片段将从载入的 xml 中删除第一个 <book> 元素：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 把变量 y 设置为要删除的元素节点
- 通过使用 removeChild() 方法从父节点删除元素节点


## 删除自身 - 删除当前的节点

removeChild() 方法是唯一可以删除指定节点的方法。

当您已导航到需要删除的节点时，就可以通过使用 parentNode 属性和 removeChild() 方法来删除此节点：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 把变量 y 设置为要删除的元素节点
- 通过使用 parentNode 属性和 removeChild() 方法来删除此元素节点


## 删除文本节点

removeChild() 方法可用于删除文本节点：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 把变量 x 设置为第一个 title 元素节点
- 把变量 y 设置为要删除的文本节点
- 通过使用 removeChild() 方法从父节点删除元素节点

不太常用 removeChild() 从节点删除文本。可以使用 nodeValue 属性代替它。请看下一段。


## 清空文本节点

nodeValue 属性可用于改变或清空文本节点的值：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 把变量 x 设置为第一个 title 元素的文本节点
- 使用 nodeValue 属性来清空文本节点的文本

遍历并更改所有 <title> 元素的文本节点： 尝试一下


## 根据名称删除属性节点

removeAttribute(name) 方法用于根据名称删除属性节点。

实例：removeAttribute('category')

下面的代码片段删除第一个 <book> 元素中的 "category" 属性：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 使用 getElementsByTagName() 来获取 book 节点
- 从第一个 book 元素节点中删除 "category" 属性

遍历并删除所有 <book> 元素的 "category" 属性： 尝试一下


## 根据对象删除属性节点

removeAttributeNode(node) 方法通过使用 node 对象作为参数，来删除属性节点。

实例: removeAttributeNode(x)

下面的代码片段删除所有 <book> 元素的所有属性：


## 实例

```java
xmlDoc=loadXMLDoc("books.xml");

x=xmlDoc.getElementsByTagName("book");

for (i=0;i<x.length;i++)
{
  while (x[i].attributes.length>0)
  {
    attnode=x[i].attributes[0];
    old_att=x[i].removeAttributeNode(attnode);
  }
}
```

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 使用 getElementsByTagName() 来获取所有 book 节点
- 检查每个 book 元素是否拥有属性
- 如果在某个 book 元素中存在属性，则删除该属性


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM 删除节点` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
