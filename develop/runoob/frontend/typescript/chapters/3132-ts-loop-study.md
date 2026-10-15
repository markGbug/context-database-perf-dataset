# TypeScript：TypeScript 循环

- 来源：[TypeScript 循环](https://www.runoob.com/typescript/ts-loop.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3132

## 本章内容

有的时候，我们可能需要多次执行同一块代码。一般情况下，语句是按顺序执行的：函数中的第一个语句先执行，接着是第二个语句，依此类推。

编程语言提供了更为复杂执行路径的多种控制结构。

循环语句允许我们多次执行一个语句或语句组，下面是大多数编程语言中循环语句的流程图：


## for 循环

TypeScript for 循环用于多次执行一个语句序列，简化管理循环变量的代码。


### 语法

语法格式如下所示：

```java
for ( init; condition; increment ){
    statement(s);
}
```

下面是 for 循环的控制流程解析：

- init 会首先被执行，且只会执行一次。这一步允许您声明并初始化任何循环控制变量。您也可以不在这里写任何语句，只要有一个分号出现即可。
- 接下来，会判断 condition。如果为 true，则执行循环主体。如果为 false，则不执行循环主体，且控制流会跳转到紧接着 for 循环的下一条语句。
- 在执行完 for 循环主体后，控制流会跳回上面的 increment 语句。该语句允许您更新循环控制变量。该语句可以留空，只要在条件后有一个分号出现即可。
- 条件再次被判断。如果为 true，则执行循环，这个过程会不断重复（循环主体，然后增加步值，再然后重新判断条件）。在条件变为 false 时，for 循环终止。

在这里，statement(s) 可以是一个单独的语句，也可以是几个语句组成的代码块。

condition 可以是任意的表达式，当条件为 true 时执行循环，当条件为 false 时，退出循环。


### 流程图


### 实例

以下实例计算 5 的阶乘， for 循环生成从 5 到 1 的数字，并计算每次循环数字的乘积。


## TypeScript

```java
var num:number = 5;
var i:number;
var factorial = 1;

for(i = num;i>=1;i--) {
   factorial *= i;
}
console.log(factorial)
```

编译以上代码得到如下 JavaScript 代码：


## JavaScript

```java
var num = 5;
var i;
var factorial = 1;
for (i = num; i >= 1; i--) {
    factorial *= i;
}
console.log(factorial);
```

执行以上 JavaScript 代码，输出结果为：

```text
120
```


## for...in 循环

for...in 语句用于一组值的集合或列表进行迭代输出。


### 语法

语法格式如下所示：

```java
for (var val in list) {
    //语句
}
```


### 实例


## TypeScript

```java
var j:any;
var n:any = "a b c"

for(j in n) {
    console.log(n[j])
}
```

编译以上代码得到如下 JavaScript 代码：


## JavaScript

```java
var j;
var n = "a b c";
for (j in n) {
    console.log(n[j]);
}
```

执行以上 JavaScript 代码，输出结果为：

```text
a

b

c
```


## 复习重点

- 能说明 `TypeScript 循环` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
