# C#：C# 属性（Property）

- 来源：[C# 属性（Property）](https://www.runoob.com/csharp/csharp-property.html)
- 分类：后端开发
- 技术：C#
- 笔记类型：学习笔记
- 章节序号：0781

## 本章内容

C# 中的属性（Property）是类和结构体中用于封装数据的成员。它们提供了一种方式来定义类成员的访问和设置规则，通常用于隐藏字段（Fields）的内部实现细节，同时提供控制数据访问的机制。

属性可以看作是对字段的包装器，通常由 get 和 set 访问器组成。

属性（Property）不会确定存储位置。相反，它们具有可读写或计算它们值的 访问器（accessors）。

例如，有一个名为 Student 的类，带有 age、name 和 code 的私有域。我们不能在类的范围以外直接访问这些域，但是我们可以拥有访问这些私有域的属性。


### 基本语法

```java
public class Person
{
    private string name;

    public string Name
    {
        get { return name; }
        set { name = value; }
    }
}
```

以上代码中，Name 属性封装了私有字段 name。get 访问器用于获取字段值，而 set 访问器用于设置字段值。


### 自动实现的属性

如果你只需要一个简单的属性，C# 允许使用自动实现的属性，这样你不需要显式地定义字段。

```java
public class Person
{
    public string Name { get; set; }
}
```

在这种情况下，编译器会自动为 Name 属性生成一个私有的匿名字段来存储值。


### 只读属性

如果你只需要一个只读属性，可以省略 set 访问器。

```java
public class Person
{
    public string Name { get; }

    public Person(string name)
    {
        Name = name;
    }
}
```


### 只写属性

类似地，如果你只需要一个只写属性，可以省略 get 访问器。

```java
public class Person
{
    private string name;

    public string Name
    {
        set { name = value; }
    }
}
```


### 自定义逻辑

你可以在 get 和 set 访问器中包含自定义的逻辑。

```java
public class Person
{
    private string name;

    public string Name
    {
        get { return name; }
        set
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("Name cannot be empty.");
            name = value;
        }
    }
}
```


### 计算属性

属性也可以是计算的，不依赖于字段。

```java
public class Rectangle
{
    public int Width { get; set; }
    public int Height { get; set; }

    public int Area
    {
        get { return Width * Height; }
    }
}
```


## 访问器（Accessors）

属性（Property）的访问器（accessor）包含有助于获取（读取或计算）或设置（写入）属性的可执行语句。访问器（accessor）声明可包含一个 get 访问器、一个 set 访问器，或者同时包含二者。例如：


## 实例

下面的实例演示了属性（Property）的用法：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
Student Info: Code = 001, Name = Zara, Age = 9
Student Info: Code = 001, Name = Zara, Age = 10
```


## 抽象属性（Abstract Properties）

抽象类可拥有抽象属性，这些属性应在派生类中被实现。下面的程序说明了这点：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
Student Info: Code = 001, Name = Zara, Age = 9
Student Info: Code = 001, Name = Zara, Age = 10
```


## 复习重点

- 能说明 `C# 属性（Property）` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
