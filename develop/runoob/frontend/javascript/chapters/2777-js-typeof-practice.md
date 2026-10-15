# JavaScript：JavaScript typeof, null, 和 undefined

- 来源：[JavaScript typeof](https://www.runoob.com/js/js-typeof.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：练习笔记
- 章节序号：2777

## 本章内容

## typeof 操作符

你可以使用 typeof 操作符来检测变量的数据类型。


## 实例

在JavaScript中，数组是一种特殊的对象类型。 因此 typeof [1,2,3,4] 返回 object。

正确检测数组的方法：

```text
Array.isArray([1,2,3]); // true
[1,2,3] instanceof Array; // true
```

typeof 是 JavaScript 中的一个操作符，用于返回给定变量的数据类型。

完整类型检测表:

检测未定义变量：

```text
if (typeof variable === "undefined") {...}
```

检测函数是否存在：

```text
if (typeof myFunction === "function") {...}
```

注意数组和null的特殊情况：

```text
// 正确检测数组
if (Array.isArray(myVar)) {...}

// 正确检测null
if (myVar === null) {...}
```


## null

在 JavaScript 中 null 表示 "什么都没有"。

null是一个只有一个值的特殊类型。表示一个空对象引用。

你可以设置为 null 来清空对象:


## 实例

你可以设置为 undefined 来清空对象:


## 实例


## undefined

在 JavaScript 中, undefined 是一个没有设置值的变量。

typeof 一个没有值的变量会返回 undefined。


## 实例

任何变量都可以通过设置值为 undefined 来清空。 类型为 undefined.


## 实例


## undefined 和 null 的区别


## 实例

null 和 undefined 的值相等，但类型不等：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `JavaScript typeof` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
