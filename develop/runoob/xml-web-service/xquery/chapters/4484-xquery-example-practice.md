# XQuery：XQuery 实例

- 来源：[XQuery 实例](https://www.runoob.com/xquery/xquery-example.html)
- 分类：XML / Web Service
- 技术：XQuery
- 笔记类型：练习笔记
- 章节序号：4484

## 本章内容

在本节，让我们通过研究一个例子来学习一些基础的 XQuery 语法。


## XML 实例文档

我们将在下面的例子中使用这个 XML 文档。

"books.xml":

在您的浏览器中查看 "books.xml" 文件。


## 如何从 "books.xml" 选取节点？


### 函数

XQuery 使用函数来提取 XML 文档中的数据。

doc() 用于打开 "books.xml" 文件：


### 路径表达式

XQuery 使用路径表达式在 XML 文档中通过元素进行导航。

下面的路径表达式用于在 "books.xml" 文件中选取所有的 title 元素：

(/bookstore 选取 bookstore 元素，/book 选取 bookstore 元素下的所有 book 元素，而 /title 选取每个 book 元素下的所有 title 元素)

上面的 XQuery 可提取以下数据：


### 谓语

XQuery 使用谓语来限定从 XML 文档所提取的数据。

下面的谓语用于选取 bookstore 元素下的所有 book 元素，并且所选取的 book 元素下的 price 元素的值必须小于 30：

上面的 XQuery 可提取到下面的数据：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XQuery 实例` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
