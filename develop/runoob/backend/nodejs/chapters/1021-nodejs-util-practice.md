# Node.js：Node.js 常用工具

- 来源：[Node.js 常用工具](https://www.runoob.com/nodejs/nodejs-util.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：练习笔记
- 章节序号：1021

## 本章内容

util 模块是 Node.js 的一个内置模块，包含了实用工具函数，用于支持 JavaScript 编程中的调试、错误处理、格式化等功能。

util 提供常用函数的集合，用于弥补核心 JavaScript 的功能过于精简的不足。

util 模块中的功能涵盖了从对象检查、继承到格式化字符串等多个方面。


### 导入 util 模块

首先，你需要导入 util 模块：

```javascript
const util = require('util');
```

常用方法：


### util.types 下的类型检测方法

util.types 是一个包含许多类型检测方法的集合，扩展了 JavaScript 的 typeof 和 instanceof。


## 应用实例


### util.format() - 字符串格式化

util.format() 用于生成格式化字符串，支持占位符如 %s、%d 和 %j，分别代表字符串、数字和 JSON。


## 实例


### util.promisify() - 转换回调函数为 Promise

util.promisify() 将传统回调风格的函数转换为返回 Promise 的函数，从而可以与 async/await 一起使用。


## 实例


### util.callbackify() - 将 Promise 转换为回调

util.callbackify() 将返回 Promise 的函数转换为回调风格的函数，便于在需要回调的代码环境中使用。

util.callbackify(original) 将 async 异步函数（或者一个返回值为 Promise 的函数）转换成遵循异常优先的回调风格的函数，例如将 (err, value) => ... 回调作为最后一个参数。 在回调函数中，第一个参数为拒绝的原因（如果 Promise 解决，则为 null），第二个参数则是解决的值。


## 实例

以上代码输出结果为：

```text
hello world
```

回调函数是异步执行的，并且有异常堆栈错误追踪。 如果回调函数抛出一个异常，进程会触发一个 'uncaughtException' 异常，如果没有被捕获，进程将会退出。

null 在回调函数中作为一个参数有其特殊的意义，如果回调函数的首个参数为 Promise 拒绝的原因且带有返回值，且值可以转换成布尔值 false，这个值会被封装在 Error 对象里，可以通过属性 reason 获取。

```javascript
function fn() {
  return Promise.reject(null);
}
const callbackFunction = util.callbackify(fn);

callbackFunction((err, ret) => {
  // 当 Promise 被以 `null` 拒绝时，它被包装为 Error 并且原始值存储在 `reason` 中。
  err && err.hasOwnProperty('reason') && err.reason === null;  // true
});
```

original 为 async 异步函数。该函数返回传统回调函数。


### util.deprecate() - 标记函数为废弃

util.deprecate() 用于标记不推荐使用的函数，调用时会显示警告信息。


## 实例


### util.types - 数据类型检测

util.types 提供了一组方法来检测特定数据类型，扩展了 typeof 和 instanceof 的功能。


## 实例


### util.inherits

util.inherits(constructor, superConstructor) 是一个实现对象间原型继承的函数。

JavaScript 的面向对象特性是基于原型的，与常见的基于类的不同。JavaScript 没有提供对象继承的语言级别特性，而是通过原型复制来实现的。

在这里我们只介绍 util.inherits 的用法，示例如下：

```javascript
var util = require('util');
function Base() {
    this.name = 'base';
    this.base = 1991;
    this.sayHello = function() {
    console.log('Hello ' + this.name);
    };
}
Base.prototype.showName = function() {
    console.log(this.name);
};
function Sub() {
    this.name = 'sub';
}
util.inherits(Sub, Base);
var objBase = new Base();
objBase.showName();
objBase.sayHello();
console.log(objBase);
var objSub = new Sub();
objSub.showName();
//objSub.sayHello();
console.log(objSub);
```

我们定义了一个基础对象 Base 和一个继承自 Base 的 Sub，Base 有三个在构造函数内定义的属性和一个原型中定义的函数，通过util.inherits 实现继承。运行结果如下：

```text
base
Hello base
{ name: 'base', base: 1991, sayHello: [Function] }
sub
{ name: 'sub' }
```

注意：Sub 仅仅继承了Base 在原型中定义的函数，而构造函数内部创造的 base 属 性和 sayHello 函数都没有被 Sub 继承。

同时，在原型中定义的属性不会被 console.log 作 为对象的属性输出。如果我们去掉 objSub.sayHello(); 这行的注释，将会看到：

```html
node.js:201
throw e; // process.nextTick error, or 'error' event on first tick
^
TypeError: Object #<Sub> has no method 'sayHello'
at Object.<anonymous> (/home/byvoid/utilinherits.js:29:8)
at Module._compile (module.js:441:26)
at Object..js (module.js:459:10)
at Module.load (module.js:348:31)
at Function._load (module.js:308:12)
at Array.0 (module.js:479:10)
at EventEmitter._tickCallback (node.js:192:40)
```

注意：在 ES6 出现之前，util.inherits 是 Node.js 中实现继承的主要方法。但是，ES6 之后推荐使用 class 和 extends 语法，这样继承的代码更具可读性。


### util.inspect() - 打印对象结构

util.inspect(object[, options])：将对象转换为字符串表示形式，便于调试。

util.inspect() 将对象转换为字符串形式，常用于调试，以查看对象的详细结构和属性。可以指定 options 参数来控制输出格式。


## 实例


## util.isArray(object)

如果给定的参数 "object" 是一个数组返回 true，否则返回 false。

```javascript
var util = require('util');

util.isArray([])
  // true
util.isArray(new Array)
  // true
util.isArray({})
  // false
```


## util.isRegExp(object)

如果给定的参数 "object" 是一个正则表达式返回true，否则返回false。

```javascript
var util = require('util');

util.isRegExp(/some regexp/)
  // true
util.isRegExp(new RegExp('another regexp'))
  // true
util.isRegExp({})
  // false
```


## util.isDate(object)

如果给定的参数 "object" 是一个日期返回true，否则返回false。

```javascript
var util = require('util');

util.isDate(new Date())
  // true
util.isDate(Date())
  // false (without 'new' returns a String)
util.isDate({})
  // false
```

更多详情可以访问 http://nodejs.org/api/util.html 了解详细内容。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Node.js 常用工具` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
