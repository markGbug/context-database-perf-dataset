# XML DOM：XML DOM 替换节点

- 来源：[DOM 替换节点](https://www.runoob.com/dom/dom-nodes-replace.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：练习笔记
- 章节序号：4388

## 本章内容

replaceChild() 方法替换指定节点。

nodeValue 属性替换文本节点中的文本。


## 尝试一下 - 实例

下面的实例使用 XML 文件 books.xml。 函数 loadXMLDoc()，位于外部 JavaScript 中，用于加载 XML 文件。

替换元素节点 本例使用 replaceChild() 来替换第一个 <book> 节点。

替换文本节点中的数据 本例使用 nodeValue 属性来替换文本节点中的数据。


## 替换元素节点

replaceChild() 方法用于替换节点。

下面的代码片段替换第一个 <book> 元素：


## 实例

```text
xmlDoc=loadXMLDoc("books.xml");

x=xmlDoc.documentElement;

// 创建新的 book 元素, title 元素及 node 节点
newNode=xmlDoc.createElement("book");
newTitle=xmlDoc.createElement("title");
newText=xmlDoc.createTextNode("A Notebook");

// 将 text 节点添加到 title 节点中
newTitle.appendChild(newText);
// 将 title 节点添加到  book 节点中
newNode.appendChild(newTitle);

y=xmlDoc.getElementsByTagName("book")[0]
// 使用新节点替换第一个 book 节点
x.replaceChild(newNode,y);
```

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 创建一个新的元素节点 <book>
- 创建一个新的元素节点 <title>
- 创建一个新的文本节点，带有文本 "A Notebook"
- 向新元素节点 <title> 追加这个新文本节点
- 向新元素节点 <book> 追加这个新元素节点 <title>
- 把第一个 <book> 元素节点替换为新的 <book> 元素节点


## 替换文本节点中的数据

replaceData() 方法用于替换文本节点中的数据。

replaceData() 方法有三个参数：

- offset - 在何处开始替换字符。offset 值以 0 开始。
- length - 要替换多少字符
- string - 要插入的字符串


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取第一个 <title> 元素节点的文本节点
- 使用 replaceData 方法把文本节点的前 8 个字符替换为 "Easy"


## 使用 nodeValue 属性代替

用 nodeValue 属性来替换文本节点中数据会更加容易。

下面的代码片段将用 "Easy Italian" 替换第一个 <title> 元素中的文本节点值：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取第一个 <title> 元素节点的文本节点
- 使用 nodeValue 属性来更改这个文本节点的文本

您可以在改变节点这一章中阅读更多有关更改节点值的内容。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM 替换节点` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
