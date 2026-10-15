# TypeScript：TypeScript String（字符串）

- 来源：[TypeScript String](https://www.runoob.com/typescript/ts-string.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3140

## 本章内容

在 TypeScript 中，字符串（String）是用于表示文本数据的基本数据类型，它继承并扩展了 JavaScript 的字符串特性，同时增加了静态类型校验。


### 语法

```javascript
var txt = new String("string");
```

或者更简单方式：

```javascript
var txt = "string";
```


### 两种创建方式及核心区别

TypeScript 中创建字符串有两种方式，但二者在类型、性能和使用场景上有本质区别：

方式 1：字符串字面量（推荐）

这是 TypeScript/JavaScript 中最常用、性能最优的方式，创建的是原始字符串类型（string），也是 TypeScript 类型系统中默认的字符串类型。

```javascript
// 原始字符串（推荐使用）
const txt1: string = "Hello TypeScript"; // 显式指定类型
const txt2 = "Hello JavaScript"; // 类型推导为 string
```

方式 2：String 对象（不推荐）

通过 new String() 创建的是包装对象类型（String），本质是一个对象，而非原始值，会带来类型混淆和性能损耗。

```javascript
// String 对象（不推荐）
const txtObj: String = new String("Hello Object"); // 类型为 String（对象）
```

String 对象和字符串字面量在类型上是不同的：

- 字符串字面量是基本数据类型 string，用于直接存储字符串值。
- String 对象是 String 类型，实际上是一个对象，而非原始的字符串值。


## 实例


### 字符串字面量和 String 对象的类型兼容性

在 TypeScript 中，string 字面量类型和 String 对象类型不完全兼容。

例如，string 类型的变量无法直接使用 String 对象的方法，反之亦然。因此，通常情况下不需要使用 String 对象。


## 实例

strLiteral 是原始字符串类型（string），而 strObject 是 String 对象类型（String）。这意味着它们的类型不同。

以上代码转为 JavaScript 代码为：


## 实例


### String 对象属性

下表列出了 String 对象支持的属性：

对创建该对象的函数的引用。

```javascript
var str = new String( "This is string" );
console.log("str.constructor is:" + str.constructor)
```

输出结果：

```javascript
str.constructor is:function String() { [native code] }
```

返回字符串的长度。

```javascript
var uname = new String("Hello World")
console.log("Length "+uname.length)  // 输出 11
```

允许您向对象添加属性和方法。

```javascript
function employee(id:number,name:string) {
    this.id = id
    this.name = name
 }
 var emp = new employee(123,"admin")
 employee.prototype.email="admin@runoob.com" // 添加属性 email
 console.log("员工号: "+emp.id)
 console.log("员工姓名: "+emp.name)
 console.log("员工邮箱: "+emp.email)
```


### String 方法

下表列出了 String 对象支持的方法：

返回在指定位置的字符。

```javascript
var str = new String("RUNOOB");
console.log("str.charAt(0) 为:" + str.charAt(0)); // R
console.log("str.charAt(1) 为:" + str.charAt(1)); // U
console.log("str.charAt(2) 为:" + str.charAt(2)); // N
console.log("str.charAt(3) 为:" + str.charAt(3)); // O
console.log("str.charAt(4) 为:" + str.charAt(4)); // O
console.log("str.charAt(5) 为:" + str.charAt(5)); // B
```

返回在指定的位置的字符的 Unicode 编码。

```javascript
var str = new String("RUNOOB");
console.log("str.charCodeAt(0) 为:" + str.charCodeAt(0)); // 82
console.log("str.charCodeAt(1) 为:" + str.charCodeAt(1)); // 85
console.log("str.charCodeAt(2) 为:" + str.charCodeAt(2)); // 78
console.log("str.charCodeAt(3) 为:" + str.charCodeAt(3)); // 79
console.log("str.charCodeAt(4) 为:" + str.charCodeAt(4)); // 79
console.log("str.charCodeAt(5) 为:" + str.charCodeAt(5)); // 66
```

连接两个或更多字符串，并返回新的字符串。

```javascript
var str1 = new String( "RUNOOB" );
var str2 = new String( "GOOGLE" );
var str3 = str1.concat( str2 );
console.log("str1 + str2 : "+str3) // RUNOOBGOOGLE
```

返回某个指定的字符串值在字符串中首次出现的位置。

```javascript
var str1 = new String( "RUNOOB" );

var index = str1.indexOf( "OO" );
console.log("查找的字符串位置 :" + index );  // 3
```

从后向前搜索字符串，并从起始位置（0）开始计算返回字符串最后出现的位置。

```javascript
var str1 = new String( "This is string one and again string" );
var index = str1.lastIndexOf( "string" );
console.log("lastIndexOf 查找到的最后字符串位置 :" + index ); // 29

index = str1.lastIndexOf( "one" );
console.log("lastIndexOf 查找到的最后字符串位置 :" + index ); // 15
```

用本地特定的顺序来比较两个字符串。

```javascript
var str1 = new String( "This is beautiful string" );

var index = str1.localeCompare( "This is beautiful string");

console.log("localeCompare first :" + index );  // 0
```

match()

查找找到一个或多个正则表达式的匹配。

```javascript
var str="The rain in SPAIN stays mainly in the plain";
var n=str.match(/ain/g);  // ain,ain,ain
```

替换与正则表达式匹配的子串

```javascript
var re = /(\w+)\s(\w+)/;
var str = "zara ali";
var newstr = str.replace(re, "$2, $1");
console.log(newstr); // ali, zara
```

检索与正则表达式相匹配的值

```javascript
var re = /apples/gi;
var str = "Apples are round, and apples are juicy.";
if (str.search(re) == -1 ) {
   console.log("Does not contain Apples" );
} else {
   console.log("Contains Apples" );
}
```

提取字符串的片断，并在新的字符串中返回被提取的部分。

把字符串分割为子字符串数组。

```javascript
var str = "Apples are round, and apples are juicy.";
var splitted = str.split(" ", 3);
console.log(splitted)  // [ 'Apples', 'are', 'round,' ]
```

从起始索引号提取字符串中指定数目的字符。

提取字符串中两个指定的索引号之间的字符。

```javascript
var str = "RUNOOB GOOGLE TAOBAO FACEBOOK";
console.log("(1,2): "    + str.substring(1,2));   // U
console.log("(0,10): "   + str.substring(0, 10)); // RUNOOB GOO
console.log("(5): "      + str.substring(5));     // B GOOGLE TAOBAO FACEBOOK
```

根据主机的语言环境把字符串转换为小写，只有几种语言（如土耳其语）具有地方特有的大小写映射。

```javascript
var str = "Runoob Google";
console.log(str.toLocaleLowerCase( ));  // runoob google
```


### String 对象的使用建议

在 TypeScript 中，使用 String 对象通常是不必要的，直接使用 string 字面量会更高效且符合 TypeScript 的最佳实践：

- 性能：String 对象是一个引用类型，会占用更多内存，且每次创建一个新对象性能开销更大。
- 类型安全：TypeScript 更鼓励使用 string 字面量类型，保持代码的简洁和一致性。

如果确实需要使用 String 对象的方法，可以通过 valueOf() 方法将对象转为原始字符串，然后继续处理。

通常情况下，TypeScript 推荐直接使用 string 字面量类型，以简化代码，提高性能，避免不必要的类型转换和复杂性。


## 实例


## 复习重点

- 能说明 `TypeScript String` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
