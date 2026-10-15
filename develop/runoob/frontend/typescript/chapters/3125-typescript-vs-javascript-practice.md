# TypeScript：TypeScript vs JavaScript 对比

- 来源：[TypeScript vs JavaScript](https://www.runoob.com/typescript/typescript-vs-javascript.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3125

## 本章内容

TypeScript 和 JavaScript 是前端开发中两个最重要的语言，理解它们之间的区别对于现代 Web 开发至关重要。

JavaScript 是 Web 的原生脚本语言，而 TypeScript 是 JavaScript 的超集，添加了类型系统和其他高级特性。


## 核心区别


## 类型系统对比

JavaScript 是动态类型语言，变量类型在运行时确定：


## JavaScript 动态类型

TypeScript 是静态类型语言，在编译时检查类型：


## TypeScript 静态类型


## 编译过程

TypeScript 需要编译为 JavaScript 才能在浏览器中运行：


## TypeScript 源码

编译后的 JavaScript：


## 编译后的 JavaScript


## 类型推断

TypeScript 具有强大的类型推断能力，即使不显式声明类型：


## 类型推断


## 开发体验对比


### 智能提示

TypeScript 为 IDE 提供丰富的类型信息，实现智能提示：

```text
// 在 TypeScript 中，IDE 知道 user 对象有 name 和 age 属性
user.    // 自动提示 .name 和 .age

// JavaScript 中 IDE 无法确定类型，提示有限
user.    // 可能没有有用的提示
```


### 重构支持

TypeScript 使得代码重构更安全：

- 重命名变量/函数时，所有引用自动更新
- 修改函数签名时，调用处会显示错误
- 提取代码时，类型自动保持


## 选择 TypeScript 的理由

为什么选择 TypeScript：

- 编译时错误检测，提前发现 bug
- 更好的代码可读性和可维护性
- 强大的 IDE 智能提示
- 安全的重构
- 现代前端框架的标配（React、Vue、Angular）

TypeScript 是 JavaScript 的超集，它在保持 JavaScript 灵活性的同时，增加了类型系统来提高代码质量。对于大型项目，TypeScript 的优势更加明显。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript vs JavaScript` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
