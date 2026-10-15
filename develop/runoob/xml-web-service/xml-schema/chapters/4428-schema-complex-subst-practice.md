# XML Schema：XSD 元素替换(Element Substitution)

- 来源：[XML Schema 元素替换](https://www.runoob.com/schema/schema-complex-subst.html)
- 分类：XML / Web Service
- 技术：XML Schema
- 笔记类型：练习笔记
- 章节序号：4428

## 本章内容

通过 XML Schema，一个元素可对另一个元素进行替换。


## 元素替换

让我们举例说明：我们的用户来自英国和挪威。我们希望有能力让用户选择在 XML 文档中使用挪威语的元素名称还是英语的元素名称。

为了解决这个问题，我们可以在 XML schema 中定义一个 substitutionGroup。首先，我们声明主元素，然后我们会声明次元素，这些次元素可声明它们能够替换主元素。

在上面的例子中，"name" 元素是主元素，而 "navn" 元素可替代 "name" 元素。

请看一个 XML schema 的片段：

有效的 XML 文档类似这样（根据上面的 schema）：

或类似这样：


## 阻止元素替换

为防止其他的元素替换某个指定的元素，请使用 block 属性：

请看某个 XML schema 的片段：

合法的 XML 文档应该类似这样（根据上面的 schema）：

但是下面的文档不再合法：


## 使用 substitutionGroup

可替换元素的类型必须和主元素相同，或者从主元素衍生而来。假如可替换元素的类型与主元素的类型相同，那么您就不必规定可替换元素的类型了。

请注意，substitutionGroup 中的所有元素（主元素和可替换元素）必须被声明为全局元素，否则就无法工作！


## 什么是全局元素（Global Elements）？

全局元素指 "schema" 元素的直接子元素！本地元素（Local elements）指嵌套在其他元素中的元素。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `XML Schema 元素替换` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
