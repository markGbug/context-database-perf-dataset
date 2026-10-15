# XML DOM：XML DOM 添加节点

- 来源：[DOM 添加节点](https://www.runoob.com/dom/dom-nodes-add.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：练习笔记
- 章节序号：4390

## 本章内容

## 尝试一下 - 实例

下面的实例使用 XML 文件 books.xml。 函数 loadXMLDoc()，位于外部 JavaScript 中，用于加载 XML 文件。

在最后一个子节点之后添加一个节点 本例使用 appendChild() 方法向一个已有的节点添加一个子节点。

在指定的子节点之前添加一个节点 本例使用 insertBefore() 方法在一个指定的子节点之前插入一个节点。

添加一个新属性 本例使用 setAttribute() 方法添加一个新的属性。

向文本节点添加数据 本例使用 insertData() 把数据插入一个已有的文本节点中。


## 添加节点 - appendChild()

appendChild() 方法向一个已有的节点添加一个子节点。

新节点会添加（追加）到任何已有的子节点之后。

注意：如果节点的位置很重要，请使用 insertBefore() 方法。

下面的代码片段创建一个元素（<edition>），并把它添加到第一个 <book> 元素的最后一个子节点后面：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 创建一个新节点 <edition>
- 把这个节点追加到第一个 <book> 元素

遍历并向所有 <book> 元素追加一个元素：尝试一下


## 插入节点 - insertBefore()

insertBefore()方法用于在指定的子节点之前插入节点。

在被添加的节点的位置很重要时，此方法很有用：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 创建一个新的元素节点 <book>
- 把这个新节点插到最后一个 <book> 元素节点之前

如果 insertBefore() 的第二个参数是 null，新节点将被添加到最后一个已有的子节点之后。

x.insertBefore(newNode,null) 和 x.appendChild(newNode) 都可以向 x 追加一个新的子节点。


## 添加新属性

addAtribute() 这个方法是不存在的。

如果属性不存在，则 setAttribute() 可创建一个新的属性：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 把第一个 <book> 元素的 "edition" 属性的值设置（创建）为 "first"

注意：如果属性已存在，setAttribute() 方法将覆盖已有的值。


## 向文本节点添加文本 - insertData()

insertData() 方法将数据插入已有的文本节点中。

insertData() 方法有两个参数：

- offset - 在何处开始插入字符（以 0 开始）
- string - 要插入的字符串

下面的代码片段将把 "Easy" 添加到已加载的 XML 的第一个 <title> 元素的文本节点：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM 添加节点` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
