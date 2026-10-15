# TypeScript：TypeScript 函数

- 来源：[TypeScript 函数](https://www.runoob.com/typescript/ts-function.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3133

## 本章内容

函数是一组一起执行一个任务的语句。

您可以把代码划分到不同的函数中。如何划分代码到不同的函数中是由您来决定的，但在逻辑上，划分通常是根据每个函数执行一个特定的任务来进行的。

函数声明告诉编译器函数的名称、返回类型和参数。函数定义提供了函数的实际主体。


## 函数定义

函数就是包裹在花括号中的代码块，前面使用了关键词 function：

语法格式如下所示：

```javascript
function function_name()
{
    // 执行代码
}
```


### 实例


## TypeScript

```javascript
function () {
    // 函数定义
    console.log("调用函数")
}
```


## 调用函数

函数只有通过调用才可以执行函数内的代码。

语法格式如下所示：

```text
function_name()
```


### 实例


## TypeScript

```javascript
function test() {   // 函数定义
    console.log("调用函数")
}
test()              // 调用函数
```


## 函数返回值

有时，我们会希望函数将执行的结果返回到调用它的地方。

通过使用 return 语句就可以实现。

在使用 return 语句时，函数会停止执行，并返回指定的值。

语法格式如下所示：

```javascript
function function_name():return_type {
    // 语句
    return value;
}
```

- return_type 是返回值的类型。
- return 关键词后跟着要返回的结果。
- 一般情况下，一个函数只有一个 return 语句。
- 返回值的类型需要与函数定义的返回类型(return_type)一致。


### 实例


## TypeScript

```javascript
// 函数定义
function greet():string { // 返回一个字符串
    return "Hello World"
}

function caller() {
    var msg = greet() // 调用 greet() 函数
    console.log(msg)
}

// 调用函数
caller()
```

- 实例中定义了函数 greet()，返回值的类型为 string。
- greet() 函数通过 return 语句返回给调用它的地方，即变量 msg，之后输出该返回值。。

编译以上代码，得到以下 JavaScript 代码：


## JavaScript

```javascript
// 函数定义
function greet() {
    return "Hello World";
}
function caller() {
    var msg = greet(); // 调用 greet() 函数
    console.log(msg);
}
// 调用函数
caller();
```


## 带参数函数

在调用函数时，您可以向其传递值，这些值被称为参数。

这些参数可以在函数中使用。

您可以向函数发送多个参数，每个参数使用逗号 , 分隔：

语法格式如下所示：

```javascript
function func_name( param1 [:datatype], param2 [:datatype]) {
}
```

- param1、param2 为参数名。
- datatype 为参数类型。


### 实例


## TypeScript

```javascript
function add(x: number, y: number): number {
    return x + y;
}
console.log(add(1,2))
```

- 实例中定义了函数 add()，返回值的类型为 number。
- add() 函数中定义了两个 number 类型的参数，函数内将两个参数相加并返回。

编译以上代码，得到以下 JavaScript 代码：


## JavaScript

```javascript
function add(x, y) {
    return x + y;
}
console.log(add(1, 2));
```

输出结果为：

```text
3
```


## 可选参数和默认参数


### 可选参数

在 TypeScript 函数里，如果我们定义了参数，则我们必须传入这些参数，除非将这些参数设置为可选，可选参数使用问号标识 ？。

实例


## TypeScript

```javascript
function buildName(firstName: string, lastName: string) {
    return firstName + " " + lastName;
}

let result1 = buildName("Bob");                  // 错误，缺少参数
let result2 = buildName("Bob", "Adams", "Sr.");  // 错误，参数太多了
let result3 = buildName("Bob", "Adams");         // 正确
```

以下实例，我们将 lastName 设置为可选参数：


## TypeScript

```javascript
function buildName(firstName: string, lastName?: string) {
    if (lastName)
        return firstName + " " + lastName;
    else
        return firstName;
}

let result1 = buildName("Bob");  // 正确
let result2 = buildName("Bob", "Adams", "Sr.");  // 错误，参数太多了
let result3 = buildName("Bob", "Adams");  // 正确
```

可选参数必须跟在必需参数后面。 如果上例我们想让 firstName 是可选的，lastName 必选，那么就要调整它们的位置，把 firstName 放在后面。

如果都是可选参数就没关系。


### 默认参数

我们也可以设置参数的默认值，这样在调用函数的时候，如果不传入该参数的值，则使用默认参数，语法格式为：

```javascript
function function_name(param1[:type],param2[:type] = default_value) {
}
```

实例

以下实例函数的参数 rate 设置了默认值为 0.50，调用该函数时如果未传入参数则使用该默认值：


## TypeScript

```javascript
function calculate_discount(price:number,rate:number = 0.50) {
    var discount = price * rate;
    console.log("计算结果: ",discount);
}
calculate_discount(1000)
calculate_discount(1000,0.30)
```

编译以上代码，得到以下 JavaScript 代码：


## JavaScript

```javascript
function calculate_discount(price, rate) {
    if (rate === void 0) { rate = 0.50; }
    var discount = price * rate;
    console.log("计算结果: ", discount);
}
calculate_discount(1000);
calculate_discount(1000, 0.30);
```

输出结果为：

```text
计算结果:  500
计算结果:  300
```


## 剩余参数

有一种情况，我们不知道要向函数传入多少个参数，这时候我们就可以使用剩余参数来定义。

剩余参数语法允许我们将一个不确定数量的参数作为一个数组传入。


## TypeScript

```javascript
function buildName(firstName: string, ...restOfName: string[]) {
    return firstName + " " + restOfName.join(" ");
}

let employeeName = buildName("Joseph", "Samuel", "Lucas", "MacKinzie");
```

函数的最后一个命名参数 restOfName 以 ... 为前缀，它将成为一个由剩余参数组成的数组，索引值从0（包括）到 restOfName.length（不包括）。


## TypeScript

```java
function addNumbers(...nums:number[]) {
    var i;
    var sum:number = 0;

    for(i = 0;i<nums.length;i++) {
       sum = sum + nums[i];
    }
    console.log("和为：",sum)
 }
 addNumbers(1,2,3)
 addNumbers(10,10,10,10,10)
```

编译以上代码，得到以下 JavaScript 代码：


## 后续章节

- JavaScript
- 匿名函数
- 实例
- TypeScript
- JavaScript
- TypeScript
- JavaScript
- 匿名函数自调用
- TypeScript
- JavaScript
- 构造函数
- 实例
- TypeScript
- JavaScript
- 递归函数
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript 函数` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
