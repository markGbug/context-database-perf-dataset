# C#：C# 命名空间（Namespace）

- 来源：[C# 命名空间（Namespace）](https://www.runoob.com/csharp/csharp-namespace.html)
- 分类：后端开发
- 技术：C#
- 笔记类型：练习笔记
- 章节序号：0774

## 本章内容

命名空间的设计目的是提供一种让一组名称与其他名称分隔开的方式。在一个命名空间中声明的类的名称与另一个命名空间中声明的相同的类的名称不冲突。

我们举一个计算机系统中的例子，一个文件夹(目录)中可以包含多个文件夹，每个文件夹中不能有相同的文件名，但不同文件夹中的文件可以重名。


## 定义命名空间

命名空间的定义是以关键字 namespace 开始，后跟命名空间的名称，如下所示：

为了调用支持命名空间版本的函数或变量，会把命名空间的名称置于前面，如下所示：

```text
namespace_name.item_name;
```

下面的程序演示了命名空间的用法：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
Inside first_space
Inside second_space
```


## using 关键字

using 关键字表明程序使用的是给定命名空间中的名称。例如，我们在程序中使用 System 命名空间，其中定义了类 Console。我们可以只写：

```text
Console.WriteLine ("Hello there");
```

我们可以写完全限定名称，如下：

```text
System.Console.WriteLine("Hello there");
```

您也可以使用 using 命名空间指令，这样在使用的时候就不用在前面加上命名空间名称。该指令告诉编译器随后的代码使用了指定命名空间中的名称。下面的代码演示了命名空间的应用。

让我们使用 using 指定重写上面的实例：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
Inside first_space
Inside second_space
```


## 嵌套命名空间

命名空间可以被嵌套，即您可以在一个命名空间内定义另一个命名空间，如下所示：

```text
namespace namespace_name1
{
   // 代码声明
   namespace namespace_name2
   {
     // 代码声明
   }
}
```

您可以使用点（.）运算符访问嵌套的命名空间的成员，如下所示：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
In SomeNameSpace
In Nested
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C# 命名空间（Namespace）` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
