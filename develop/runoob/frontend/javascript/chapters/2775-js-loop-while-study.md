# JavaScript：JavaScript while 循环

- 来源：[JavaScript while 循环](https://www.runoob.com/js/js-loop-while.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2775

## 本章内容

只要指定条件为 true，循环就可以一直执行代码块。


## while 循环

while 循环会在指定条件为真时循环执行代码块。


### 语法


### 实例

本例中的循环将继续运行，只要变量 i 小于 5：


## 实例

```java
while (i<5)
{
    x=x + "The number is " + i + "<br>";
    i++;
}
```


## do/while 循环

do/while 循环是 while 循环的变体。该循环会在检查条件是否为真之前执行一次代码块，然后如果条件为真的话，就会重复这个循环。


### 语法


### 实例

下面的例子使用 do/while 循环。该循环至少会执行一次，即使条件为 false 它也会执行一次，因为代码块会在条件被测试前执行：


## 实例

```java
do
{
    x=x + "The number is " + i + "<br>";
    i++;
}
while (i<5);
```

别忘记增加条件中所用变量的值，否则循环永远不会结束！


## 比较 for 和 while

如果您已经阅读了前面那一章关于 for 循环的内容，您会发现 while 循环与 for 循环很像。

本例中的循环使用 for 循环来显示 cars 数组中的所有值：


## 实例

```java
cars=["BMW","Volvo","Saab","Ford"];
var i=0;
for (;cars[i];)
{
    document.write(cars[i] + "<br>");
    i++;
}
```

本例中的循环使用 while 循环来显示 cars 数组中的所有值：


## 实例

```java
cars=["BMW","Volvo","Saab","Ford"];
var i=0;
while (cars[i])
{
    document.write(cars[i] + "<br>");
    i++;
}
```


## 复习重点

- 能说明 `JavaScript while 循环` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
