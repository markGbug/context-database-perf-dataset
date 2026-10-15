# TypeScript：TypeScript 元组

- 来源：[TypeScript 元组](https://www.runoob.com/typescript/ts-tuple.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3150

## 本章内容

我们知道数组中元素的数据类型都一般是相同的（any[] 类型的数组可以不同），如果存储的元素数据类型不同，则需要使用元组。

TypeScript 中的元组（Tuple）是一种特殊类型的数组，它允许在数组中存储不同类型的元素，与普通数组不同，元组中的每个元素都有明确的类型和位置。元组可以在很多场景下用于表示固定长度、且各元素类型已知的数据结构。

创建元组的语法格式如下：

```javascript
let tuple: [类型1, 类型2, 类型3, ...];
```

### 实例

声明一个元组并初始化：

```javascript
let mytuple: [number, string];
mytuple = [42,"Runoob"];
```

在上面的例子中，mytuple 是一个元组，它包含一个 number 类型和一个 string 类型的元素。

### 访问元组

元组中元素使用索引来访问，第一个元素的索引值为 0，第二个为 1，以此类推第 n 个为 n-1，语法格式如下:

```text
tuple_name[index]
```

### 实例

以下实例定义了元组，包含了数字和字符串两种类型的元素：

## TypeScript

```javascript
let mytuple: [number, string, boolean] = [42, "Runoob", true];

// 访问元组中的元素
let num = mytuple[0]; // 访问第一个元素，值为 42，类型为 number
let str = mytuple[1]; // 访问第二个元素，值为 "Runoob"，类型为 string
let bool = mytuple[2]; // 访问第三个元素，值为 true，类型为 boolean

console.log(num);  // 输出: 42
console.log(str);  // 输出: Runoob
console.log(bool); // 输出: true
```

编译以上代码，得到以下 JavaScript 代码：

## JavaScript

```javascript
var mytuple = [42, "Runoob", true];
// 访问元组中的元素
var num = mytuple[0]; // 访问第一个元素，值为 42，类型为 number
var str = mytuple[1]; // 访问第二个元素，值为 "Runoob"，类型为 string
var bool = mytuple[2]; // 访问第三个元素，值为 true，类型为 boolean
console.log(num); // 输出: 42
console.log(str); // 输出: Runoob
console.log(bool); // 输出: true
```

输出结果为：

```text
42
Runoob
true
```

## 元组运算

我们可以使用以下两个函数向元组添加新元素或者删除元素：

push() 向元组添加元素，添加在最后面。

pop() 从元组中移除元素（最后一个），并返回移除的元素。

push 方法可以向元组的末尾添加一个元素，类型必须符合元组定义中的类型约束。如果超出元组的类型约束，TypeScript 会报错。

## TypeScript

```javascript
var tuple = [42, "Hello"];
// 添加符合类型的元素
tuple.push("World"); // 合法，因为元组定义了可选的 string 类型
console.log(tuple); // 输出: [42, "Hello", "World"]
```

编译以上代码，得到以下 JavaScript 代码：

## JavaScript

```javascript
var tuple = [42, "Hello"];
// 添加符合类型的元素
tuple.push("World"); // 合法，因为元组定义了可选的 string 类型
console.log(tuple); // 输出: [42, "Hello", "World"]
```

输出结果为：

```text
[ 42, 'Hello', 'World' ]
```

pop 方法从元组的末尾移除一个元素，并返回该元素。返回的元素类型将根据元组的定义类型推断。

## 实例

## 更新元组

元组是可变的，这意味着我们可以对元组进行更新操作：

## TypeScript

```javascript
var mytuple = [42, "Runoob", "Taobao", "Google"]; // 创建一个元组
console.log("元组的第一个元素为：" + mytuple[0])

// 更新元组元素
mytuple[0] = 121
console.log("元组中的第一个元素更新为："+ mytuple[0])
```

编译以上代码，得到以下 JavaScript 代码：

## JavaScript

```javascript
var mytuple = [42, "Runoob", "Taobao", "Google"]; // 创建一个元组
console.log("元组的第一个元素为：" + mytuple[0]);
// 更新元组元素
mytuple[0] = 121;
console.log("元组中的第一个元素更新为：" + mytuple[0]);
```

输出结果为：

```text
元组的第一个元素为：42
元组中的第一个元素更新为：121
```

## 解构元组

我们也可以把元组元素赋值给变量，如下所示：

## TypeScript

```javascript
let a: [number, string, boolean] = [42, "Hello", true];// 创建一个元组

var [b,c] = a
console.log( b )
console.log( c )
```

编译以上代码，得到以下 JavaScript 代码：

## JavaScript

```javascript
var a = [42, "Hello", true]; // 创建一个元组
var b = a[0], c = a[1];
console.log(b);
console.log(c);
```

输出结果为：

```text
42
Hello
```

## 使用标签元组

TypeScript 还允许为元组中的每个元素添加标签，这使得元组的含义更加清晰：

```javascript
let tuple: [id: number, name: string] = [1, "John"];
```

在这个例子中，id 和 name 是元组的标签，可以让代码更加可读。

## 元组的实际应用

元组常用于函数返回多个值的场景，或者表示某些固定结构的数据，比如：

## 实例

## 元组的类型推断

TypeScript 可以根据数组的元素自动推断出元组的类型：

```javascript
let tuple = [42, "Hello"] as const; // 元组类型：[42, "Hello"]
```

通过 as const 断言，TypeScript 会将该元组视为一个不可变的常量元组。

## 连接元组

元组可以使用数组的 concat 方法进行连接，但需要注意连接后的结果是一个普通的数组，而不是元组。

## 实例

## 切片元组

你可以使用数组的 slice 方法对元组进行切片操作，返回一个新的数组。

## 实例

## 遍历元组

你可以使用 for...of 循环或者 forEach 方法遍历元组中的元素。

## 实例

## 转换为普通数组

虽然元组是一个固定长度、固定类型的数组，但可以通过 Array.prototype 的方法将其转换为普通数组进行进一步处理。

## 实例

## 扩展元组

使用剩余运算符可以轻松地将多个元组合并成一个新的元组：

## 实例

## 动手验证

- 复现 `TypeScript 元组` 中的关键示例或命令。
- 修改一个输入、参数或条件，观察结果变化。
- 记录报错信息、定位过程和修复方式。
