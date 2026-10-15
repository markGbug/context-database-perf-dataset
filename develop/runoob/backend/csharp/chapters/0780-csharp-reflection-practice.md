# C#：C# 反射（Reflection）

- 来源：[C# 反射（Reflection）](https://www.runoob.com/csharp/csharp-reflection.html)
- 分类：后端开发
- 技术：C#
- 笔记类型：练习笔记
- 章节序号：0780

## 本章内容

反射指程序可以访问、检测和修改它本身状态或行为的一种能力。

程序集包含模块，而模块包含类型，类型又包含成员。反射则提供了封装程序集、模块和类型的对象。

您可以使用反射动态地创建类型的实例，将类型绑定到现有对象，或从现有对象中获取类型。然后，可以调用类型的方法或访问其字段和属性。


### 优缺点

优点：

- 1、反射提高了程序的灵活性和扩展性。
- 2、降低耦合性，提高自适应能力。
- 3、它允许程序创建和控制任何类的对象，无需提前硬编码目标类。

缺点：

- 1、性能问题：使用反射基本上是一种解释操作，用于字段和方法接入时要远慢于直接代码。因此反射机制主要应用在对灵活性和拓展性要求很高的系统框架上，普通程序不建议使用。
- 2、使用反射会模糊程序内部逻辑；程序员希望在源代码中看到程序的逻辑，反射却绕过了源代码的技术，因而会带来维护的问题，反射代码比相应的直接代码更复杂。


## 反射（Reflection）的用途

反射（Reflection）有下列用途：

- 它允许在运行时查看特性（attribute）信息。
- 它允许审查集合中的各种类型，以及实例化这些类型。
- 它允许延迟绑定的方法和属性（property）。
- 它允许在运行时创建新类型，然后使用这些类型执行一些任务。


## 查看元数据

我们已经在上面的章节中提到过，使用反射（Reflection）可以查看特性（attribute）信息。

System.Reflection 类的 MemberInfo 对象需要被初始化，用于发现与类相关的特性（attribute）。为了做到这点，您可以定义目标类的一个对象，如下：

```text
System.Reflection.MemberInfo info = typeof(MyClass);
```

下面的程序演示了这点：


## 实例

当上面的代码被编译和执行时，它会显示附加到类 MyClass 上的自定义特性：

```text
HelpAttribute
```


## 实例

在本实例中，我们将使用在上一章中创建的 DeBugInfo 特性，并使用反射（Reflection）来读取 Rectangle 类中的元数据。


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
Length: 4.5
Width: 7.5
Area: 33.75
Bug No: 49
Developer: Nuha Ali
Last Reviewed: 10/10/2012
Remarks: Unused variable
Bug No: 45
Developer: Zara Ali
Last Reviewed: 12/8/2012
Remarks: Return type mismatch
Bug No: 55, for Method: GetArea
Developer: Zara Ali
Last Reviewed: 19/10/2012
Remarks: Return type mismatch
Bug No: 56, for Method: Display
Developer: Zara Ali
Last Reviewed: 19/10/2012
Remarks:
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C# 反射（Reflection）` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
