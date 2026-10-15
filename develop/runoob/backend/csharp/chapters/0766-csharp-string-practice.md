# C#：C# 字符串（String）

- 来源：[C# 字符串（String）](https://www.runoob.com/csharp/csharp-string.html)
- 分类：后端开发
- 技术：C#
- 笔记类型：练习笔记
- 章节序号：0766

## 本章内容

在 C# 中，您可以使用字符数组来表示字符串，但是，更常见的做法是使用 string 关键字来声明一个字符串变量。string 关键字是 System.String 类的别名。


## 创建 String 对象

您可以使用以下方法之一来创建 string 对象：

- 通过给 String 变量指定一个字符串
- 通过使用 String 类构造函数
- 通过使用字符串串联运算符（ + ）
- 通过检索属性或调用一个返回字符串的方法
- 通过格式化方法来转换一个值或对象为它的字符串表示形式

下面的实例演示了这点：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
Full Name: RowanAtkinson
Greetings: Hello
Message: Hello From Tutorials Point
Message: Message sent at 17:58 on Wednesday, 10 October 2012
```


## String 类的属性

String 类有以下两个属性：


## String 类的方法

String 类有许多方法用于 string 对象的操作。下面的表格提供了一些最常用的方法：

上面的方法列表并不详尽，请访问 MSDN 库，查看完整的方法列表和 String 类构造函数。


## 实例

下面的实例演示了上面提到的一些方法：

比较字符串


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
This is test and This is text are not equal.
```

字符串包含字符串：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
The sequence 'test' was found.
```

获取子字符串：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
Last night I dreamt of San Pedro
San Pedro
```

连接字符串：


## 实例

当上面的代码被编译和执行时，它会产生下列结果：

```text
Down the way nights are dark
And the sun shines daily on the mountain top
I took a trip on a sailing ship
And when I reached Jamaica
I made a stop
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C# 字符串（String）` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
