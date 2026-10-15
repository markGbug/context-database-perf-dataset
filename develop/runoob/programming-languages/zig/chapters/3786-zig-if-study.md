# Zig：Zig 流程控制

- 来源：[Zig 流程控制](https://www.runoob.com/zig/zig-if.html)
- 分类：编程语言
- 技术：Zig
- 笔记类型：学习笔记
- 章节序号：3786

## 本章内容

Zig 编程语言流程控制语句通过程序设定一个或多个条件语句来设定。

在条件为 true 时执行指定程序代码，在条件为 false 时执行其他指定代码。

以下是典型的流程控制流程图：

Zig 提供了以下控制结构语句：


## if 语句


### 语法

基本的 if 语句包含一个条件和一个与之相关联的代码块，如果条件为真（true），则执行代码块。

```text
if (<condition) {
    // 如果 condition 为 true，执行这里的代码
}
```

if-else 语句在基本 if 语句的基础上增加了一个 else 分支，如果 if 中的条件为假（false），则执行 else 分支中的代码。

```html
if (<condition>) {
    // 如果 condition 为 true，执行这里的代码
} else {
    // 如果 condition 为 false，执行这里的代码
}
```

condition：一个布尔表达式。如果条件为 true，则执行第一个代码块；否则执行 else 代码块。


## 实例

编译执行输出结果为：

```text
x is greater than 5
```


## if-else...else 语句


### 语法

支持多个条件检查，按顺序检查每个条件，直到某个条件为 true 并执行相应的代码块。


## 实例


## 实例

编译执行输出结果为：

```text
x is equal to 10
```


## 嵌套的 if-else

if-else 语句可以嵌套使用，这意味着你可以在 if 或 else 分支中再包含一个 if 语句。

```text
if (<条件1>) {
    // 如果条件1为真，执行这里的代码
    if (<条件2>) {
        // 如果条件1和条件2都为真，执行这里的代码
    } else {
        // 如果条件1为真但条件2为假，执行这里的代码
    }
} else {
    // 如果条件1为假，执行这里的代码
}
```


## 实例

编译执行输出结果为：

```text
Input is between 5 and 10
```


## if 语句中的类型推导

Zig 编译器可以推导出 if 语句中变量的类型，如果条件表达式的结果是一个布尔值。

```javascript
const condition = true;
if (condition) {
    // 这里 condition 的类型是 bool，编译器自动推导
}
```


## 复习重点

- 能说明 `Zig 流程控制` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
