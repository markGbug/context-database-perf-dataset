# JavaScript：JavaScript 变量

- 来源：[JavaScript 变量](https://www.runoob.com/js/js-variables.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2762

## 本章内容

变量是用于存储信息的"容器"。

在 JavaScript 中，变量用于存储数据，并可以在程序执行过程中动态更改。

在 JavaScript 中，变量可以存储各种类型的数据，如数字、字符串、对象、函数等。

变量名是标识符，用于引用存储在变量中的数据。

在 JavaScript 中，可以使用 var、let 和 const 关键字来声明变量。

- var：ES5 引入的变量声明方式，具有函数作用域。
- let：ES6 引入的变量声明方式，具有块级作用域。
- const：ES6 引入的常量声明方式，具有块级作用域，且值不可变。


## 实例

```javascript
var x=5;
var y=6;
var z=x+y;
```


### 就像代数那样

x=5 y=6 z=x+y

在代数中，我们使用字母（比如 x）来保存值（比如 5）。

通过上面的表达式 z=x+y，我们能够计算出 z 的值为 11。

在 JavaScript 中，这些字母被称为变量。


## JavaScript 变量

与代数一样，JavaScript 变量可用于存放值（比如 x = 5）和表达式（比如 z = x + y）。

变量可以使用短名称（比如 x 和 y），也可以使用描述性更好的名称（比如 age, sum, totalvolume）。

- 变量必须以字母开头
- 变量也能以 $ 和 _ 符号开头（不过我们不推荐这么做）
- 变量名称对大小写敏感（y 和 Y 是不同的变量）


## JavaScript 数据类型

JavaScript 变量还能保存其他数据类型，比如文本值 (name="Bill Gates")。

在 JavaScript 中，类似 "Bill Gates" 这样一条文本被称为字符串。

JavaScript 变量有很多种类型，但是现在，我们只关注数字和字符串。

当您向变量分配文本值时，应该用双引号或单引号包围这个值。

当您向变量赋的值是数值时，不要使用引号。如果您用引号包围数值，该值会被作为文本来处理。


## 实例

```javascript
var pi=3.14;
// 如果你熟悉 ES6，pi 可以使用 const 关键字，表示一个常量
// const pi = 3.14;
var person="John Doe";
var answer='Yes I am!';
```


## 声明（创建） JavaScript 变量

在 JavaScript 中创建变量通常称为"声明"变量。

我们使用 var 关键词来声明变量：

```javascript
var carname;
```

变量声明之后，该变量是空的（它没有值）。

如需向变量赋值，请使用等号：

```text
carname="Volvo";
```

不过，您也可以在声明变量时对其赋值：

```javascript
var carname="Volvo";
```

在下面的例子中，我们创建了名为 carname 的变量，并向其赋值 "Volvo"，然后把它放入 id="demo" 的 HTML 段落中：


## 实例

```javascript
var carname="Volvo";
document.getElementById("demo").innerHTML=carname;
```

var 声明特点：

- 变量可以重复声明（覆盖原变量）。
- 变量未赋值时，默认值为 undefined。
- var 声明的变量会提升（Hoisting），但不会初始化。


## 一条语句，多个变量

您可以在一条语句中声明很多变量。该语句以 var 开头，并使用逗号分隔变量即可：

```javascript
var lastname="Doe", age=30, job="carpenter";
```

声明也可横跨多行：

```javascript
var lastname="Doe",
age=30,
job="carpenter";
```

一条语句中声明的多个变量不可以同时赋同一个值:

```javascript
var x, y, z = 1;
```

x, y 为 undefined， z 为 1。


## Value = undefined

在计算机程序中，经常会声明无值的变量。未使用值来声明的变量，其值实际上是 undefined。

在执行过以下语句后，变量 carname 的值将是 undefined：

```javascript
var carname;
```


## 重新声明 JavaScript 变量

如果重新声明 JavaScript 变量，该变量的值不会丢失：

在以下两条语句执行后，变量 carname 的值依然是 "Volvo"：

```javascript
var
carname="Volvo";
var carname;
```


## JavaScript 算数

您可以通过 JavaScript 变量来做算数，使用的是 = 和 + 这类运算符：


## 实例

```text
y=5;
x=y+2;
```


## 使用 let 和 const (ES6)

在 2015 年以前，我们使用 var 关键字来声明 JavaScript 变量。

在 2015 后的 JavaScript 版本 (ES6) 允许我们使用 const 关键字来定义一个常量，使用 let 关键字定义的限定范围内作用域的变量。


### let

let 是 ES6 引入的新变量声明方式，推荐使用。

let 语法：

```javascript
let variableName = value;
```


## 实例


### const

const 用于定义常量，即一旦赋值后，变量的值不能再被修改。

const 语法：

```javascript
const variableName = value;
```


## 实例

更多 const 和 let 内容可以参阅：JavaScript let 和 const。

Safari 10 和 Edge 14 是第一批支持 ES6 所有特性的浏览器：

您将在本教程稍后的章节学到更多有关 JavaScript 运算符的知识。


## 复习重点

- 能说明 `JavaScript 变量` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
