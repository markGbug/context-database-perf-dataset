# TypeScript：TypeScript 类继承与多态

- 来源：[TypeScript 类继承与多态](https://www.runoob.com/typescript/ts-class-inheritance.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：学习笔记
- 章节序号：3171

## 本章内容

TypeScript 支持面向对象编程的继承和多态特性。


## 类的继承

使用 extends 关键字实现继承。


## 实例

运行结果：

```text
旺财 汪汪汪!
```


## super 关键字

super 用于调用父类的方法和构造函数。


## 实例

运行结果：

```text
这是一个 红色的图形，半径是 5
面积: 78.54
```


## 多态

子类的实例可以赋值给父类类型。


## 实例

运行结果：

```text
小白 喵喵喵!
旺财 汪汪汪!
动物 发出声音
```


## instanceof 检查

使用 instanceof 检查实例类型。


## 实例

运行结果：

```text
矩形面积: 20
圆形面积: 28.27
```


## protected 成员

protected 成员在子类中可见。


## 实例

运行结果：

```text
我是 Alice，在 技术部 工作
```


## 总结

- 继承：extends 关键字
- super：调用父类
- 多态：同一接口不同实现
- protected：子类可见


## 复习重点

- 能说明 `TypeScript 类继承与多态` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
