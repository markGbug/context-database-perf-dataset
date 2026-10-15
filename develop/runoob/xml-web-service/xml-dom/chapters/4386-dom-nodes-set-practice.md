# XML DOM：XML DOM 改变节点值

- 来源：[DOM 改变节点](https://www.runoob.com/dom/dom-nodes-set.html)
- 分类：XML / Web Service
- 技术：XML DOM
- 笔记类型：练习笔记
- 章节序号：4386

## 本章内容

nodeValue 属性用于改变节点值。

setAttribute() 方法用于改变属性值。


## 尝试一下 - 实例

下面的实例使用 XML 文件 books.xml。 函数 loadXMLDoc()，位于外部 JavaScript 中，用于加载 XML 文件。

改变元素的文本节点 本例使用 nodeValue 属性来改变 "books.xml" 中第一个 <title> 元素的文本节点。

通过使用 setAttribute 来改变属性值 本例使用 setAttribute() 方法来改变第一个 <book> 的 "category" 属性的值。

通过使用 nodeValue 来改变属性值 本例使用 nodeValue 属性来改变第一个 <book> 的 "category" 属性的值。


## 改变元素的值

在 DOM 中，每种成分都是节点。元素节点没有文本值。

元素节点的文本存储在子节点中。该节点称为文本节点。

改变元素文本的方法，就是改变这个子节点（文本节点）的值。


## 改变文本节点的值

nodeValue 属性可用于改变文本节点的值。

下面的代码片段改变了第一个 <title> 元素的文本节点值：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取第一个 <title> 元素的文本节点
- 把该文本节点的节点值更改为 "Easy Cooking"

遍历并更改所有 <title> 元素的文本节点： 尝试一下


## 改变属性的值

在 DOM 中，属性也是节点。与元素节点不同，属性节点拥有文本值。I

改变属性的值的方法，就是改变它的文本值。

可以通过使用 setAttribute() 方法或属性节点的 nodeValue 属性来完成这个任务。


## 通过使用 setAttribute() 改变属性

setAttribute() 方法改变已有属性的值，或创建新属性。

下面的代码改变 <book> 元素的 category 属性：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取第一个 <book> 元素
- 把 "category" 属性的值更改为 "food"

遍历所有的 <title> 元素并添加一个新属性： 尝试一下

注意：如果属性不存在，则创建一个新属性（拥有指定的名称和值）。


## 通过使用 nodeValue 改变属性

nodeValue 属性可用于更改属性节点的值：


## 实例

实例解释：

- 使用 loadXMLDoc() 把 "books.xml" 载入 xmlDoc 中
- 获取第一个 <book> 元素的 "category" 属性
- 把该属性节点的值更改为 "food"


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `DOM 改变节点` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
