# JavaScript：JavaScript 模板字符串

- 来源：[JavaScript 字符串模板](https://www.runoob.com/js/js-string-templates.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2769

## 本章内容

JavaScript 中的模板字符串是一种方便的字符串语法，允许你在字符串中嵌入表达式和变量。

模板字符串使用反引号 `` 作为字符串的定界符分隔的字面量。

模板字面量是用反引号（`）分隔的字面量，允许多行字符串、带嵌入表达式的字符串插值和一种叫带标签的模板的特殊结构。


### 语法

```text
`string text`

`string text line 1
 string text line 2`

`string text ${expression} string text`

tagFunction`string text ${expression} string text`
```

参数

- string text：将成为模板字面量的一部分的字符串文本。几乎允许所有字符，包括换行符和其他空白字符。但是，除非使用了标签函数，否则无效的转义序列将导致语法错误。
- expression：要插入当前位置的表达式，其值被转换为字符串或传递给 tagFunction。
- tagFunction：如果指定，将使用模板字符串数组和替换表达式调用它，返回值将成为模板字面量的值。


## 实例


### 浏览器支持

模板字面量是 ES6 新特性 (JavaScript 2015)，目前一些最新版本浏览器都支持：

模板字符串中可以同时使用单引号和双引号：


## 实例

```javascript
let text = `He's often called "Runoob"`;
```

模板字符串还支持多行文本，而无需使用特殊的转义字符：


## 实例

若要转义模板字面量中的反引号（`），需在反引号之前加一个反斜杠（\）。

```text
`\`` === "`"; // true
```

模板字面量用反引号（`）括起来，而不是双引号（"）或单引号（'）。

除了普通字符串外，模板字面量还可以包含占位符——一种由美元符号和大括号分隔的嵌入式表达式：${expression}。

字符串和占位符被传递给一个函数（要么是默认函数，要么是自定义函数）。默认函数（当未提供自定义函数时）只执行字符串插值来替换占位符，然后将这些部分拼接到一个字符串中。

模板字符串中允许我们使用变量：


## 实例

```javascript
const name = 'Runoob';
const age = 30;
const message = `My name is ${name} and I'm ${age} years old.`;
```

以上实例中，${name} 和 ${age} 是模板字符串的表达式部分，它们被包含在 ${} 内部，并在运行时求值。

模板字符串允许你在字符串中引用变量、执行函数调用和进行任意的JavaScript表达式。

模板字符串中允许我们使用表达式：


## 实例

模板字符串当作 HTML 模板使用：


## 实例


## 复习重点

- 能说明 `JavaScript 字符串模板` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
