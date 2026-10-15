# 知识点 77128：XML DOM：DOM 替换节点 - 实例

- 来源：[DOM 替换节点](https://www.runoob.com/dom/dom-nodes-replace.html)
- 来源章节：[4388-dom-nodes-replace-practice.md](../chapters/4388-dom-nodes-replace-practice.md)
- 分类：XML / Web Service
- 技术：XML DOM
- 所在小节：实例
- 知识类型：代码
- 原章节序号：4388

## 原文片段

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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `实例` 这一小节和 `DOM 替换节点` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
