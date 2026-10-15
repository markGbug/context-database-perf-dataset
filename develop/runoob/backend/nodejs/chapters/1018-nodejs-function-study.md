# Node.js：Node.js 函数

- 来源：[Node.js 函数](https://www.runoob.com/nodejs/nodejs-function.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：学习笔记
- 章节序号：1018

## 本章内容

函数是一段可重复使用的代码块，用于执行特定任务。

在 Node.js 中，函数是 JavaScript 的核心组成部分之一，是构建应用程序的基本单元。

Node.js 继承了 JavaScript 的所有函数特性，并在其异步编程模型中发挥了重要作用。

在 JavaScript中，一个函数可以作为另一个函数的参数。我们可以先定义一个函数，然后传递，也可以在传递参数的地方直接定义函数。


### 函数的重要性

- 代码复用：避免重复编写相同逻辑
- 模块化：将复杂问题分解为小函数
- 可维护性：便于调试和修改独立功能单元


### 函数声明

使用 function 关键字声明一个函数。

```javascript
function greet(name) {
    console.log(`Hello, ${name}!`);
}
```


### 函数表达式

将函数赋值给一个变量。

```javascript
const greet = function(name) {
    console.log(`Hello, ${name}!`);
};
```


### 箭头函数

ES6 引入的简洁函数表达式。

```javascript
const greet = (name) => {
    console.log(`Hello, ${name}!`);
};

// 单行箭头函数
const greet = name => console.log(`Hello, ${name}!`);
```


### 函数的类型

1、普通函数

最常见的函数形式，可以有参数和返回值。

```javascript
function add(a, b) {
    return a + b;
}
```

2、匿名函数

没有名字的函数，通常作为参数传递给其他函数。

```javascript
setTimeout(function() {
    console.log('This is an anonymous function.');
}, 1000);
```

3、回调函数

作为参数传递给另一个函数，并在某个操作完成后被调用。

```javascript
function fetchData(callback) {
    setTimeout(() => {
        const data = 'Some data';
        callback(data);
    }, 1000);
}

fetchData((data) => {
    console.log(data);
});
```


### 异步函数

从回调到 Promise。


## 实例

使用 async 和 await 关键字处理异步操作。


## 实例


### 调用方式对比


## 高级用法

1、闭包

闭包是指一个函数能够记住并访问其词法作用域，即使这个函数在其词法作用域之外执行。


## 实例

2、高阶函数

接受函数作为参数或返回函数的函数。


## 实例


## 函数参数处理


### 默认参数

在函数声明时为参数提供默认值。

```javascript
function greet(name = 'Guest') {
    console.log(`Hello, ${name}!`);
}

greet(); // Hello, Guest!
greet('Alice'); // Hello, Alice!
```


### 剩余参数

允许将不定数量的参数表示为一个数组。


## 实例


### 解构参数

从对象或数组中提取数据并将其赋值给变量。


## 实例


## 实例

函数单一职责：每个函数应该只做一件事，这样更容易测试和维护。


## 实例

避免全局变量：尽量减少全局变量的使用，使用局部变量和函数参数。


## 实例

使用箭头函数：箭头函数简洁明了，特别是在处理回调函数时。


## 实例

错误处理： 使用 try...catch 语句处理可能抛出的错误。


## 实例

函数作为参数: 函数作为一个参数来使用。


## 实例

以上代码中，我们把 say 函数作为 execute 函数的第一个变量进行了传递。这里传递的不是 say 的返回值，而是 say 本身！

这样一来， say 就变成了execute 中的本地变量 someFunction ，execute 可以通过调用 someFunction() （带括号的形式）来使用 say 函数。

当然，因为 say 有一个变量， execute 在调用 someFunction 时可以传递这样一个变量。

匿名函数：我们可以把一个函数作为变量传递。但是我们不一定要绕这个"先定义，再传递"的圈子，我们可以直接在另一个函数的括号中定义和传递这个函数：


## 后续章节

- 实例
- 函数传递是如何让 HTTP 服务器工作的
- 实例
- 实例
- 函数最佳实践
- 函数设计原则
- 性能优化技巧
- 实例
- 实战练习
- 练习1：创建温度转换函数
- 实例
- 练习2：实现简单的事件发射器
- 实例

## 复习重点

- 能说明 `Node.js 函数` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
