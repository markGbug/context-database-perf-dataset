# TypeScript：TypeScript 混入（Mixin）

- 来源：[TypeScript 混入](https://www.runoob.com/typescript/ts-mixin.html)
- 分类：前端开发
- 技术：TypeScript
- 笔记类型：练习笔记
- 章节序号：3164

## 本章内容

混入（Mixin）是一种代码复用模式，用于将多个独立的功能模块混入到一个类中。

TypeScript 通过泛型函数返回扩展类的方式实现 Mixin，弥补了单继承无法复用多个来源行为的不足。


## 基本概念

Mixin 的核心是一个接收基类、返回扩展类的泛型函数。Constructor 类型约束用于描述"任意可被继承的类"。


## 实例

运行结果：

```text
Alice
true
```

注意：Mixin 不修改原始类，而是返回一个全新的扩展类，原始的 User 类不受影响。


## 组合多个 Mixin

将多个 Mixin 函数嵌套调用，即可将多份能力依次叠加到同一个类上。


## 实例

运行结果：

```text
[LOG] {"name":"Phone","price":999,"createdAt":"2026-..."}
true
```


## Mixin 与接口结合

Mixin 返回的类可以声明实现某个接口，使消费方通过接口类型操作混入后的对象，而不依赖具体实现。


## 实例

运行结果：

```text
{"title":"TypeScript 入门","content":"正文内容..."}
{"title":"TypeScript 进阶","content":"正文内容..."}
false
```


## 带约束的 Mixin

通过泛型约束，可以限定 Mixin 只能混入满足特定条件的类，避免运行时缺少必要属性。


## 实例

运行结果：

```text
[42] Keyboard
```


## Mixin 与继承的对比


## 总结

- 核心模式：Mixin 是接收基类、返回扩展类的泛型函数，Constructor<T> 是标准约束类型
- 能力叠加：嵌套调用多个 Mixin 函数即可将多份能力组合到同一个类
- 接口结合：Mixin 返回的类可以实现接口，消费方只需依赖接口而非具体类
- 泛型约束：通过约束 TBase 可以限定 Mixin 的适用范围，在编译期阻止错误使用
- 适用场景：日志、序列化、克隆、时间戳等横切关注点，优于多层继承


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `TypeScript 混入` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
