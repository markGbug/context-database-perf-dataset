# TypeScript：TypeScript 基础类型

- 来源：[TypeScript 基础类型](https://www.runoob.com/typescript/ts-type.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3128

## 本章内容

基础类型可以开发者更准确地描述数据的结构和意图。

TypeScript 包含的数据类型如下表:

注意：TypeScript 和 JavaScript 没有整数类型。


### 1、string 字符串

表示文本数据，只能存储字符串，通常用于描述文字信息。

```javascript
let message: string = "Hello, TypeScript!";
```

模板字符串：TypeScript 支持 模板字符串，用反引号 `（记住不是单引号 '）来定义，允许在字符串中插入变量或表达式，非常适合多行文本和拼接变量。

```javascript
let name: string = "Alice";
let greeting: string = `Hello, ${name}! Welcome to TypeScript.`;
console.log(greeting); // 输出：Hello, Alice! Welcome to TypeScript.
```


### 2、number 数字

TypeScript 使用 number 表示所有数字，包括整数和浮点数。

```javascript
let age: number = 25;
let temperature: number = 36.5;
```


### 3、boolean 布尔值

表示逻辑值 true 或 false，用于条件判断。

```java
let isCompleted: boolean = false;
```


### 4、array 数组

可以表示一组相同类型的元素。可以使用 type[] 或 Array<type> 两种方式表示。

```html
let numbers: number[] = [1, 2, 3];
let names: Array<string> = ["Alice", "Bob"];
```


### 5、tuple 元组

表示已知数量和类型的数组。每个元素可以是不同的类型，适合表示固定结构的数据。

```javascript
let person: [string, number] = ["Alice", 25];
```


### 6、enum 枚举

用来定义一组命名常量。默认情况下枚举的值从 0 开始递增。

```javascript
enum Color {
  Red,
  Green,
  Blue,
}
let favoriteColor: Color = Color.Green;
```


### 7、any 类型

以表示任何类型。适合不确定数据类型的情况，但使用时需谨慎，因为 any 会绕过类型检查。

```javascript
let randomValue: any = 42;
randomValue = "hello";
```

任意值是 TypeScript 针对编程时类型不明确的变量使用的一种数据类型，它常用于以下三种情况。

1、变量的值会动态改变时，比如来自用户的输入，任意值类型可以让这些变量跳过编译阶段的类型检查，示例代码如下：

```javascript
let x: any = 1;    // 数字类型
x = 'I am who I am';    // 字符串类型
x = false;    // 布尔类型
```

改写现有代码时，任意值允许在编译时可选择地包含或移除类型检查，示例代码如下：

```javascript
let x: any = 4;
x.ifItExists();    // 正确，ifItExists方法在运行时可能存在，但这里并不会检查
x.toFixed();    // 正确
```

定义存储各种类型数据的数组时，示例代码如下：

```javascript
let arrayList: any[] = [1, false, 'fine'];
arrayList[1] = 100;
```


### 8、void 空类型

用于没有返回值的函数。声明变量时，类型 void 意味着只能赋值 null 或 undefined。

```javascript
function logMessage(message: string): void {
  console.log(message);
}
```


### 9、null 和 undefined

null 和 undefined分别表示"空值"和"未定义"。在默认情况下，它们是所有类型的子类型，但可以通过设置 strictNullChecks 严格检查。

```javascript
let empty: null = null;
let notAssigned: undefined = undefined;
```

null

在 JavaScript 中 null 表示 "什么都没有"。

null是一个只有一个值的特殊类型。表示一个空对象引用。

用 typeof 检测 null 返回是 object。

undefined

在 JavaScript 中, undefined 是一个没有设置值的变量。

typeof 一个没有值的变量会返回 undefined。

Null 和 Undefined 是其他任何类型（包括 void）的子类型，可以赋值给其它类型，如数字类型，此时，赋值后的类型会变成 null 或 undefined。而在TypeScript中启用严格的空校验（--strictNullChecks）特性，就可以使得null 和 undefined 只能被赋值给 void 或本身对应的类型，示例代码如下：

```javascript
// 启用 --strictNullChecks
let x: number;
x = 1; // 编译正确
x = undefined;    // 编译错误
x = null;    // 编译错误
```

上面的例子中变量 x 只能是数字类型。如果一个类型可能出现 null 或 undefined， 可以用 | 来支持多种类型，示例代码如下：

```javascript
// 启用 --strictNullChecks
let x: number | null | undefined;
x = 1; // 编译正确
x = undefined;    // 编译正确
x = null;    // 编译正确
```

更多内容可以查看：JavaScript typeof, null, 和 undefined


### 10、never 类型

表示不会有返回值，通常用于抛出错误或进入无限循环的函数，表示该函数永远不会正常结束。

```javascript
function throwError(message: string): never {
  throw new Error(message);
}
```

never 是其它类型（包括 null 和 undefined）的子类型，代表从不会出现的值。这意味着声明为 never 类型的变量只能被 never 类型所赋值，在函数中它通常表现为抛出异常或无法执行到终止点（例如无限循环），示例代码如下：

```java
let x: never;
let y: number;

// 编译错误，数字类型不能转为 never 类型
x = 123;

// 运行正确，never 类型可以赋值给 never类型
x = (()=>{ throw new Error('exception')})();

// 运行正确，never 类型可以赋值给 数字类型
y = (()=>{ throw new Error('exception')})();

// 返回值为 never 的函数可以是抛出异常的情况
function error(message: string): never {
    throw new Error(message);
}

// 返回值为 never 的函数可以是无法被执行到的终止点的情况
function loop(): never {
    while (true) {}
}
```


### 11、object 对象类型

表示非原始类型的值，适用于复杂的对象结构。

```javascript
let person: object = { name: "Alice", age: 30 };
```


### 12、联合类型 (Union)

表示一个变量可以是多种类型之一。通过 | 符号实现。

```javascript
let id: string | number;
id = "123";
id = 456;
```


### 13、unknown 不确定的类型

与 any 类似，但更严格。必须经过类型检查后才能赋值给其他类型变量。

```javascript
let value: unknown = "Hello";
if (typeof value === "string") {
  let message: string = value;
}
```


### 14、类型断言 (Type Assertions)

类型断言可以让开发者明确告诉编译器变量的类型，常用于无法推断的情况。可以使用 as 或尖括号语法。

```javascript
let someValue: any = "this is a string";
let strLength: number = (someValue as string).length;
```


### 15、字面量类型

字面量类型可以让变量只能拥有特定的值，用于结合联合类型定义变量的特定状态。

```javascript
let direction: "up" | "down" | "left" | "right";
direction = "up";
```

通过这些类型，TypeScript 提供了更强的类型安全性和代码检查能力，使开发者能够更清晰、准确地表达数据和意图，减少运行时错误。


## 实例

以下实例展示了 TypeScript 中主要基础类型的定义和使用，模拟一个用户对象和相关的操作函数：


## 实例

说明：

- 枚举类型 (Role)：用于定义用户角色的命名常量 Admin、User 和 Guest。
- 接口 (User)：定义了 User 对象的结构，包括 id、username、isActive 等属性，展示了 string、number、boolean、array 和 tuple 类型的使用。
- 函数 getUserInfo：返回用户的描述信息，使用了字符串插值并结合 enum。
- 函数 printUserInfo：类型为 void，因为它仅输出信息，不返回任何值。
- 联合类型 (number | string)：用于 findUser 函数的参数，可以接受数字或字符串。
- never 类型：throwError 函数抛出错误，不会正常返回，因此使用 never 类型。
- any 类型：展示如何声明一个可以接收任何类型的变量。
- unknown 类型：类似 any，但更加安全，示例中在类型断言之前进行类型检查。
- null 和 undefined：演示空值的使用。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript 基础类型` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
