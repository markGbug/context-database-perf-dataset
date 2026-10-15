# XPath：XPath 节点

- 来源：[XPath 节点](https://www.runoob.com/xpath/xpath-nodes.html)
- 分类：XML / Web Service
- 技术：XPath
- 笔记类型：练习笔记
- 章节序号：4468

## 本章内容

## XPath 术语


### 节点

在 XPath 中，有七种类型的节点：元素、属性、文本、命名空间、处理指令、注释以及文档（根）节点。XML 文档是被作为节点树来对待的。树的根被称为文档节点或者根节点。

请看下面这个 XML 文档：

上面的XML文档中的节点例子：


### 基本值（或称原子值，Atomic value）

基本值是无父或无子的节点。

基本值的例子：


### 项目（Item）

项目是基本值或者节点。


## 节点关系


### 父（Parent）

每个元素以及属性都有一个父。

在下面的例子中，book 元素是 title、author、year 以及 price 元素的父：


### 子（Children）

元素节点可有零个、一个或多个子。

在下面的例子中，title、author、year 以及 price 元素都是 book 元素的子：


### 同胞（Sibling）

拥有相同的父的节点

在下面的例子中，title、author、year 以及 price 元素都是同胞：


### 先辈（Ancestor）

某节点的父、父的父，等等。

在下面的例子中，title 元素的先辈是 book 元素和 bookstore 元素：


### 后代（Descendant）

某个节点的子，子的子，等等。

在下面的例子中，bookstore 的后代是 book、title、author、year 以及 price 元素：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XPath 节点` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
