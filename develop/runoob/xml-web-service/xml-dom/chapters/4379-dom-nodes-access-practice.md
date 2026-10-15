# XML DOM：XML DOM - 访问节点

- 来源：[DOM 访问](https://www.runoob.com/dom/dom-nodes-access.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：练习笔记
- 章节序号：4379

## 本章内容

通过 DOM，您能够访问 XML 文档中的每个节点。


## 尝试一下 - 实例

下面的实例使用 XML 文件 books.xml。 函数 loadXMLDoc()，位于外部 JavaScript 中，用于加载 XML 文件。

使用节点列表中的索引号来访问节点 本例使用 getElementsByTagname() 方法来获取 "books.xml" 中的第三个 <title> 元素。

使用 length 属性来遍历节点 本例使用 length 属性来遍历 "books.xml" 中的所有 <title> 元素。

查看元素的节点类型 本例使用 nodeType 属性来获取 "books.xml" 中根元素的节点类型。

遍历元素节点 本例使用 nodeType 属性来处理 "books.xml" 中的元素节点。

使用节点的关系来遍历元素节点 本例使用 nodeType 属性和 nextSibling 属性来处理 "books.xml" 中的元素节点。


## 访问节点

您可以通过三种方式来访问节点：

1. 通过使用 getElementsByTagName() 方法。

2. 通过循环（遍历）节点树。

3. 通过利用节点的关系在节点树中导航。


## getElementsByTagName() 方法

getElementsByTagName() 返回拥有指定标签名的所有元素。


### 语法


### 实例

下面的实例返回 x 元素下的所有 <title> 元素：

请注意，上面的实例仅返回 x 节点下的 <title> 元素。如需返回 XML 文档中的所有 <title> 元素，请使用：

在这里，xmlDoc 就是文档本身（文档节点）。


## DOM 节点列表（Node List）

getElementsByTagName() 方法返回节点列表。节点列表是节点的数组。

下面的代码使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中，然后在变量 x 中存储 <title> 节点的一个列表：

可通过索引号访问 x 中的 <title> 元素。如需访问第三个 <title>，您可以编写：

注意：该索引从 0 开始。

在本教程后面的章节中，您将学习更多有关节点列表（Node List）的知识。


## DOM 节点列表长度（Node List Length）

length 属性定义节点列表的长度（即节点的数量）。

您可以通过使用 length 属性来遍历节点列表：


## 实例

```java
xmlDoc=loadXMLDoc("books.xml");

x=xmlDoc.getElementsByTagName("title");

for (i=0;i<x.length;i++)
{
  document.write(x[i].childNodes[0].nodeValue);
  document.write("");
}
```

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取所有 <title> 元素节点
- 输出每个 <title> 元素的文本节点的值


## 节点类型（Node Types）

XML 文档的 documentElement 属性是根节点。

节点的 nodeName 属性是节点的名称。

节点的 nodeType 属性是节点的类型。

您将在本教程的下一章中学习更多有关节点属性的知识。

尝试一下


## 遍历节点

下面的代码遍历根节点的子节点，同时也是元素节点：


## 实例

```java
xmlDoc=loadXMLDoc("books.xml");

x=xmlDoc.documentElement.childNodes;

for (i=0;i<x.length;i++)
{
  if (x[i].nodeType==1)
  {
    // 执行一次
    document.write(x[i].nodeName);
    document.write("");
  }
}
```

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取根元素的子节点
- 检查每个子节点的节点类型。如果节点类型是 "1"，则是元素节点
- 如果是元素节点，则输出节点的名称


## 导航节点的关系

下面的代码使用节点关系导航节点树：


## 实例

```java
xmlDoc=loadXMLDoc("books.xml");

x=xmlDoc.getElementsByTagName("book")[0].childNodes;
y=xmlDoc.getElementsByTagName("book")[0].firstChild;

for (i=0;i<x.length;i++)
{
  if (y.nodeType==1)
  {
  // 输出节点名
  document.write(y.nodeName + "");
  }
  y=y.nextSibling;
}
```

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取第一个 book 元素的子节点
- 把 "y" 变量设置为第一个 book 元素的第一个子节点
- 对于每个子节点（第一个子节点从 "y" 开始），检查节点类型，如果节点类型为 "1"，则是元素节点
- 如果是元素节点，则输出该节点的名称
- 把 "y" 变量设置为下一个同级节点，并再次运行循环


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM 访问` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
