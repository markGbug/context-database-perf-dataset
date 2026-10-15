# JavaScript：JavaScript 数据类型

- 来源：[JavaScript 数据类型](https://www.runoob.com/js/js-datatypes.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2763

## 本章内容

值类型(基本类型)：字符串（String）、数字(Number)、布尔(Boolean)、空（Null）、未定义（Undefined）、Symbol。

引用数据类型（对象类型）：对象(Object)、数组(Array)、函数(Function)，还有两个特殊的对象：正则（RegExp）和日期（Date）。

注：Symbol 是 ES6 引入了一种新的原始数据类型，表示独一无二的值。


## JavaScript 拥有动态类型

JavaScript 拥有动态类型。这意味着相同的变量可用作不同的类型：


## 实例

变量的数据类型可以使用 typeof 操作符来查看：


## 实例

typeof [1,2,3,4] 返回 "object"，这是 JavaScript 早期设计的一个"缺陷"，数组本质上是特殊类型的对象。

正确检测数组的方法：

```text
Array.isArray([1,2,3]); // true
[1,2,3] instanceof Array; // true
```


## JavaScript 字符串

字符串是存储字符（比如 "Bill Gates"）的变量。

字符串可以是引号中的任意文本。您可以使用单引号或双引号：


## 实例

您可以在字符串中使用引号，只要不匹配包围字符串的引号即可：


## 实例

您将在本教程的高级部分学到更多关于字符串的知识。


## JavaScript 数字

JavaScript 只有一种数字类型。数字可以带小数点，也可以不带：


## 实例

极大或极小的数字可以通过科学（指数）计数法来书写：


## 实例

您将在本教程的高级部分学到更多关于数字的知识。


## JavaScript 布尔

布尔（逻辑）只能有两个值：true 或 false。

布尔常用在条件测试中。您将在本教程稍后的章节中学到更多关于条件测试的知识。


## JavaScript 数组

下面的代码创建名为 cars 的数组：

或者 (condensed array):

或者 (literal array):


## 实例

数组下标是基于零的，所以第一个项目是 [0]，第二个是 [1]，以此类推。

您将在本教程稍后的章节中学到更多关于数组的知识。


## JavaScript 对象

对象由花括号分隔。在括号内部，对象的属性以名称和值对的形式 (name : value) 来定义。属性由逗号分隔：

上面例子中的对象 (person) 有三个属性：firstname、lastname 以及 id。

空格和折行无关紧要。声明可横跨多行：

对象属性有两种寻址方式：


## 实例

您将在本教程稍后的章节中学到更多关于对象的知识。


## Undefined 和 Null

Undefined 这个值表示变量不含有值。

可以通过将变量的值设置为 null 来清空变量。


## 实例


## 声明变量类型

当您声明新变量时，可以使用关键词 "new" 来声明其类型：


## 复习重点

- 能说明 `JavaScript 数据类型` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
