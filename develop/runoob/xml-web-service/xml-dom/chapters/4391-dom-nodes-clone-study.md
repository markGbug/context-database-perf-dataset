# XML DOM：XML DOM 克隆节点

- 来源：[DOM 克隆节点](https://www.runoob.com/dom/dom-nodes-clone.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：学习笔记
- 章节序号：4391

## 本章内容

## 尝试一下 - 实例

下面的实例使用 XML 文件 books.xml。 函数 loadXMLDoc()，位于外部 JavaScript 中，用于加载 XML 文件。

复制一个节点，并把它追加到已有的节点 本例使用 cloneNode() 来复制一个节点，并把它追加到 XML 文档的根节点。


## 复制节点

cloneNode() 方法创建指定节点的副本。

cloneNode() 方法有一个参数（true 或 false）。该参数指示被克隆的节点是否包括原节点的所有属性和子节点。

下面的代码片段复制第一个 <book> 节点，并把它追加到文档的根节点：


## 实例

```java
xmlDoc=loadXMLDoc("books.xml");
x=xmlDoc.getElementsByTagName('book')[0];
cloneNode=x.cloneNode(true);
xmlDoc.documentElement.appendChild(cloneNode);

// 输出所有 title 节点文本值
y=xmlDoc.getElementsByTagName("title");
for (i=0;i<y.length;i++)
{
  document.write(y[i].childNodes[0].nodeValue);
  document.write("<br>");
}
```

输出：

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取要复制的节点
- 使用 cloneNode 方法把节点复制到 "newNode" 中
- 向 XML 文档的根节点追加新的节点
- 输出文档中所有 book 的所有 title


## 复习重点

- 能说明 `DOM 克隆节点` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
