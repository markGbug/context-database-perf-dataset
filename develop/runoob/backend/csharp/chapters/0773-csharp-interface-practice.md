# C#：C# 接口（Interface）

- 来源：[C# 接口（Interface）](https://www.runoob.com/csharp/csharp-interface.html)
- 分类：后端开发
- 技术：C#
- 笔记类型：练习笔记
- 章节序号：0773

## 本章内容

接口定义了所有类继承接口时应遵循的语法合同。接口定义了语法合同 "是什么" 部分，派生类定义了语法合同 "怎么做" 部分。

接口定义了属性、方法和事件，这些都是接口的成员。接口只包含了成员的声明。成员的定义是派生类的责任。接口提供了派生类应遵循的标准结构。

接口使得实现接口的类或结构在形式上保持一致。

抽象类在某种程度上与接口类似，但是，它们大多只是用在当只有少数方法由基类声明由派生类实现时。

接口本身并不实现任何功能，它只是和声明实现该接口的对象订立一个必须实现哪些行为的契约。

抽象类不能直接实例化，但允许派生出具体的，具有实际功能的类。


## 定义接口: MyInterface.cs

接口使用 interface 关键字声明，它与类的声明类似。接口声明默认是 public 的。下面是一个接口声明的实例：

以上代码定义了接口 IMyInterface。通常接口命名以 I 字母开头，这个接口只有一个方法 MethodToImplement()，没有参数和返回值，当然我们可以按照需求设置参数和返回值。

值得注意的是，该方法并没有具体的实现。


### 接下来我们来实现以上接口：InterfaceImplementer.cs


## 实例

InterfaceImplementer 类实现了 IMyInterface 接口，接口的实现与类的继承语法格式类似：

```text
class InterfaceImplementer : IMyInterface
```

继承接口后，我们需要实现接口的方法 MethodToImplement() , 方法名必须与接口定义的方法名一致。


## 接口继承: InterfaceInheritance.cs

以下实例定义了两个接口 IMyInterface 和 IParentInterface。

如果一个接口继承其他接口，那么实现类或结构就需要实现所有接口的成员。

以下实例 IMyInterface 继承了 IParentInterface 接口，因此接口实现类必须实现 MethodToImplement() 和 ParentInterfaceMethod() 方法：


## 实例

实例输出结果为：

```text
MethodToImplement() called.
ParentInterfaceMethod() called.
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C# 接口（Interface）` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
