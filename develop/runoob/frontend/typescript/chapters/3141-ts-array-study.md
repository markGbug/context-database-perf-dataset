# TypeScript：TypeScript Array(数组)

- 来源：[TypeScript Array(数组)](https://www.runoob.com/typescript/ts-array.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3141

## 本章内容

数组对象是使用单独的变量名来存储一系列的值。

数组非常常用。

假如你有一组数据（例如：网站名字），存在单独变量如下所示：

```javascript
var site1="Google";
var site2="Runoob";
var site3="Taobao";
```

如果有 10 个、100 个这种方式就变的很不实用，这时我们可以使用数组来解决：

```javascript
var sites:string[];
sites = ["Google","Runoob","Taobao"]
```

这样看起来就简洁多了。

TypeScript 声明数组的语法格式如下所示：

```javascript
var array_name[:datatype];        //声明
array_name = [val1,val2,valn..]   //初始化
```

或者直接在声明时初始化：

```javascript
var array_name[:datatype] = [val1,val2…valn]
```

如果数组声明时未设置类型，则会被认为是 any 类型，在初始化时根据第一个元素的类型来推断数组的类型。


### 实例

创建一个 number 类型的数组：

```javascript
var numlist:number[] = [2,4,6,8]
```

整个数组结构如下所示：

索引值第一个为 0，我们可以根据索引值来访问数组元素：


## TypeScript

```javascript
var sites:string[];
sites = ["Google","Runoob","Taobao"]
console.log(sites[0]);
console.log(sites[1]);
```

编译以上代码，得到以下 JavaScript 代码：


## JavaScript

```javascript
var sites;
sites = ["Google", "Runoob", "Taobao"];
console.log(sites[0]);
console.log(sites[1]);
```

输出结果为：

```text
Google
Runoob
```

以下实例我们在声明时直接初始化：


## TypeScript

```javascript
var nums:number[] = [1,2,3,4]
console.log(nums[0]);
console.log(nums[1]);
console.log(nums[2]);
console.log(nums[3]);
```

编译以上代码，得到以下 JavaScript 代码：


## JavaScript

```javascript
var nums = [1, 2, 3, 4];
console.log(nums[0]);
console.log(nums[1]);
console.log(nums[2]);
console.log(nums[3]);
```

输出结果为：

```text
1
2
3
4
```


## Array 对象

我们也可以使用 Array 对象创建数组。

Array 对象的构造函数接受以下两种值：

- 表示数组大小的数值。
- 初始化的数组列表，元素使用逗号分隔值。


### 实例

指定数组初始化大小：


## TypeScript

```java
var arr_names:number[] = new Array(4)

for(var i = 0; i<arr_names.length; i++) {
        arr_names[i] = i * 2
        console.log(arr_names[i])
}
```

编译以上代码，得到以下 JavaScript 代码：


## JavaScript

```java
var arr_names = new Array(4);
for (var i = 0; i < arr_names.length; i++) {
        arr_names[i] = i * 2;
        console.log(arr_names[i]);
}
```

输出结果为：

```text
0
2
4
6
```

以下实例我们直接初始化数组元素：


## TypeScript

```java
var sites:string[] = new Array("Google","Runoob","Taobao","Facebook")

for(var i = 0;i<sites.length;i++) {
        console.log(sites[i])
}
```

编译以上代码，得到以下 JavaScript 代码：


## JavaScript

```java
var sites = new Array("Google", "Runoob", "Taobao", "Facebook");
for (var i = 0; i < sites.length; i++) {
        console.log(sites[i]);
}
```

输出结果为：

```text
Google
Runoob
Taobao
Facebook
```


## 数组解构

我们也可以把数组元素赋值给变量，如下所示：


## TypeScript

```javascript
var arr:number[] = [12,13]
var[x,y] = arr // 将数组的两个元素赋值给变量 x 和 y
console.log(x)
console.log(y)
```

编译以上代码，得到以下 JavaScript 代码：


## JavaScript

```javascript
var arr = [12, 13];
var x = arr[0], y = arr[1]; // 将数组的两个元素赋值给变量 x 和 y
console.log(x);
console.log(y);
```

输出结果为：

```text
12
13
```


## 数组迭代

我们可以使用 for 语句来循环输出数组的各个元素：


## TypeScript

```java
var j:any;
var nums:number[] = [1001,1002,1003,1004]

for(j in nums) {
    console.log(nums[j])
}
```

编译以上代码，得到以下 JavaScript 代码：


## JavaScript

```java
var j;
var nums = [1001, 1002, 1003, 1004];
for (j in nums) {
    console.log(nums[j]);
}
```

输出结果为：

```text
1001
1002
1003
1004
```


## 多维数组

一个数组的元素可以是另外一个数组，这样就构成了多维数组（Multi-dimensional Array）。

最简单的多维数组是二维数组，定义方式如下：

```javascript
var arr_name:datatype[][]=[ [val1,val2,val3],[v1,v2,v3] ]
```


### 实例

定义一个二维数组，每一个维度的数组有三个元素。


## TypeScript

```javascript
var multi:number[][] = [[1,2,3],[23,24,25]]
console.log(multi[0][0])
console.log(multi[0][1])
console.log(multi[0][2])
console.log(multi[1][0])
console.log(multi[1][1])
console.log(multi[1][2])
```

编译以上代码，得到以下 JavaScript 代码：


## JavaScript

```javascript
var multi = [[1, 2, 3], [23, 24, 25]];
console.log(multi[0][0]);
console.log(multi[0][1]);
console.log(multi[0][2]);
console.log(multi[1][0]);
console.log(multi[1][1]);
console.log(multi[1][2]);
```

输出结果为：

```text
1
2
3
23
24
25
```


## 数组在函数中的使用


### 作为参数传递给函数


## TypeScript

```java
var sites:string[] = new Array("Google","Runoob","Taobao","Facebook")

function disp(arr_sites:string[]) {
        for(var i = 0;i<arr_sites.length;i++) {
                console.log(arr_sites[i])
        }
}
disp(sites);
```

编译以上代码，得到以下 JavaScript 代码：


## 后续章节

- JavaScript
- 作为函数的返回值
- TypeScript
- JavaScript
- 数组方法

## 复习重点

- 能说明 `TypeScript Array(数组)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
