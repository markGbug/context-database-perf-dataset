# 知识点 56014：TypeScript：TypeScript 接口 - TypeScript

- 来源：[TypeScript 接口](https://www.runoob.com/typescript/ts-interface.html)
- 来源章节：[3152-ts-interface-study.md](../chapters/3152-ts-interface-study.md)
- 分类：前端开发
- 技术：TypeScript
- 所在小节：TypeScript
- 知识类型：代码
- 原章节序号：3152

## 原文片段

```text
interface IPerson {
    firstName:string,
    lastName:string,
    sayHi: ()=>string
}

var customer:IPerson = {
    firstName:"Tom",
    lastName:"Hanks",
    sayHi: ():string =>{return "Hi there"}
}

console.log("Customer 对象 ")
console.log(customer.firstName)
console.log(customer.lastName)
console.log(customer.sayHi())

var employee:IPerson = {
    firstName:"Jim",
    lastName:"Blakes",
    sayHi: ():string =>{return "Hello!!!"}
}

console.log("Employee  对象 ")
console.log(employee.firstName)
console.log(employee.lastName)
```

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `TypeScript` 这一小节和 `TypeScript 接口` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
