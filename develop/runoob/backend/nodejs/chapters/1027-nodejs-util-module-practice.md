# Node.js：Node.js util 模块

- 来源：[Node.js util 模块](https://www.runoob.com/nodejs/nodejs-util-module.html)
- 分类：后端开发
- 技术：Node.js
- 笔记类型：练习笔记
- 章节序号：1027

## 本章内容

Node.js 内置模块

Node.js 中的 util 模块是一个核心模块，提供了一系列实用工具函数。这些函数主要用于帮助开发者完成常见的编程任务，如类型检查、继承实现、调试输出等。util 模块的设计初衷是弥补 JavaScript 原生功能的不足，为开发者提供更多便利。

要使用 util 模块，你只需要在代码中引入它：

```javascript
const util = require('util');
```


## util 模块的主要功能


### 1. 类型检查工具

util 模块提供了一些用于类型检查的函数，这些函数比 JavaScript 的原生 typeof 操作符更加精确和有用。

检查给定的值是否是 ArrayBuffer 实例。


## 实例

检查给定的值是否是 Date 实例。


## 实例


### 2. 实用工具函数

类似于 C 语言中的 printf 函数，用于格式化字符串。


## 实例

返回对象的字符串表示，主要用于调试。可以配置深度、颜色等选项。


## 实例


### 3. 回调风格转换

将遵循 Node.js 回调风格的函数转换为返回 Promise 的函数。


## 实例

与 promisify 相反，将返回 Promise 的函数转换为回调风格的函数。


## 实例


### 4. 继承工具

实现原型继承（ES5 风格）。注意：在 ES6 中，建议使用 class 和 extends 关键字。


## 实例


## util 模块的实际应用场景


### 1. 调试复杂对象

当需要打印复杂对象的结构时，util.inspect 比简单的 console.log 更加强大：


## 实例


### 2. 现代化旧代码

将回调风格的旧代码转换为 Promise 风格：


## 实例


### 3. 自定义对象检查

可以自定义对象的 inspect 方法，改变 util.inspect 的输出：


## 实例


## 注意事项

- 性能考虑：util.inspect 对于大型对象可能会有性能影响，生产环境中应谨慎使用。
- API 稳定性：虽然 util 模块是核心模块，但某些 API 可能仍会被标记为实验性功能。
- 现代替代方案：一些功能（如 util.inherits）在现代 JavaScript 中有更好的替代方案（如 class 语法）。
- 错误处理：使用 promisify 时，确保正确处理错误，避免未捕获的 Promise 拒绝。


## 方法与属性


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Node.js util 模块` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
