# C#：C# 匿名方法

- 来源：[C# 匿名方法](https://www.runoob.com/csharp/csharp-anonymous-methods.html)
- 分类：后端开发
- 技术：C#
- 笔记类型：概念卡
- 章节序号：0787

## 本章内容

在 C# 中，匿名函数是一种没有名字的方法，可以在代码中定义和使用。

我们已经提到过，委托是用于引用与其具有相同标签的方法。换句话说，您可以使用委托对象调用可由委托引用的方法。

匿名方法（Anonymous methods） 提供了一种传递代码块作为委托参数的技术。

在匿名方法中您不需要指定返回类型，它是从方法主体内的 return 语句推断的。


## Lambda 表达式

Lambda 表达式是一个简洁的语法，用于创建匿名函数。它们通常用于 LINQ 查询和委托。


### 语法

```text
(parameters) => expression
// 或
(parameters) => { statement; }
```


## 实例


## 匿名方法

匿名方法是通过使用 delegate 关键字创建委托实例来声明的。


### 语法

```text
delegate(parameters) { statement; }
```

例如：

```java
delegate void NumberChanger(int n);
...
NumberChanger nc = delegate(int x)
{
    Console.WriteLine("Anonymous Method: {0}", x);
};
```

代码块 Console.WriteLine("Anonymous Method: {0}", x); 是匿名方法的主体。

委托可以通过匿名方法调用，也可以通过命名方法调用，即，通过向委托对象传递方法参数。

注意: 匿名方法的主体后面需要一个 ;。

例如：

```text
nc(10);
```


## 实例


## 实例

下面的实例演示了匿名方法的概念：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
Anonymous Method: 10
Named Method: 15
Named Method: 30
```

在 C# 2.0 及更高版本中，引入了 lambda 表达式，它是一种更简洁的语法形式，用于编写匿名方法。

使用 lambda 表达式：


## 实例


## 记忆卡片

- 一句话定义：`C# 匿名方法` 是本章需要掌握的核心知识点。
- 关键要素：整理语法、输入输出、适用场景和限制条件。
- 容易混淆：把相邻概念放在一起比较，写清楚区别。
- 检索关键词：记录以后查找本章时最可能使用的关键词。
