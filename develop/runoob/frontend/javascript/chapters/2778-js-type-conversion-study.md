# JavaScript：JavaScript 类型转换

- 来源：[JavaScript 类型转换](https://www.runoob.com/js/js-type-conversion.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2778

## 本章内容

Number() 转换为数字， String() 转换为字符串， Boolean() 转换为布尔值。


## JavaScript 数据类型

在 JavaScript 中有 6 种不同的数据类型：

- string
- number
- boolean
- object
- function
- symbol

3 种对象类型：

- Object
- Date
- Array

2 个不包含任何值的数据类型：

- null
- undefined


## typeof 操作符

你可以使用 typeof 操作符来查看 JavaScript 变量的数据类型。


## 实例

请注意：

- NaN 的数据类型是 number
- 数组(Array)的数据类型是 object
- 日期(Date)的数据类型为 object
- null 的数据类型是 object
- 未定义变量的数据类型为 undefined

如果对象是 JavaScript Array 或 JavaScript Date ，我们就无法通过 typeof 来判断他们的类型，因为都是 返回 object。


## constructor 属性

constructor 属性返回所有 JavaScript 变量的构造函数。


## 实例

你可以使用 constructor 属性来查看对象是否为数组 (包含字符串 "Array"):


## 实例

你可以使用 constructor 属性来查看对象是否为日期 (包含字符串 "Date"):


## 实例


## JavaScript 类型转换

JavaScript 变量可以转换为新变量或其他数据类型：

- 通过使用 JavaScript 函数
- 通过 JavaScript 自身自动转换


## 将数字转换为字符串

全局方法 String() 可以将数字转换为字符串。

该方法可用于任何类型的数字，字母，变量，表达式：


## 实例

Number 方法 toString() 也是有同样的效果。


## 实例

在 Number 方法 章节中，你可以找到更多数字转换为字符串的方法：


## 将布尔值转换为字符串

全局方法 String() 可以将布尔值转换为字符串。

Boolean 方法 toString() 也有相同的效果。


## 将日期转换为字符串

Date() 返回字符串。

全局方法 String() 可以将日期对象转换为字符串。

Date 方法 toString() 也有相同的效果。


## 实例

在 Date 方法 章节中，你可以查看更多关于日期转换为字符串的函数：


## 将字符串转换为数字

全局方法 Number() 可以将字符串转换为数字。

字符串包含数字(如 "3.14") 转换为数字 (如 3.14).

空字符串转换为 0。

其他的字符串会转换为 NaN (不是个数字)。

在 Number 方法 章节中，你可以查看到更多关于字符串转为数字的方法：


## 一元运算符 +

Operator + 可用于将变量转换为数字：


## 实例

如果变量不能转换，它仍然会是一个数字，但值为 NaN (不是一个数字):


## 实例


## 将布尔值转换为数字

全局方法 Number() 可将布尔值转换为数字。


## 将日期转换为数字

全局方法 Number() 可将日期转换为数字。

日期方法 getTime() 也有相同的效果。


## 自动转换类型

当 JavaScript 尝试操作一个 "错误" 的数据类型时，会自动转换为 "正确" 的数据类型。

以下输出结果不是你所期望的：


## 自动转换为字符串

当你尝试输出一个对象或一个变量时 JavaScript 会自动调用变量的 toString() 方法：

数字和布尔值也经常相互转换：

下表展示了使用不同的数值转换为数字(Number), 字符串(String), 布尔值(Boolean):


## 复习重点

- 能说明 `JavaScript 类型转换` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
