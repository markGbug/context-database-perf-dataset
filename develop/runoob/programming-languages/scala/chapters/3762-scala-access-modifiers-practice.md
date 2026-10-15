# Scala：Scala 访问修饰符

- 来源：[Scala 访问修饰符](https://www.runoob.com/scala/scala-access-modifiers.html)
- 分类：编程语言
- 技术：Scala
- 笔记类型：练习笔记
- 章节序号：3762

## 本章内容

在 Scala 中，访问修饰符用于控制类、对象、特质（traits）及其成员（如字段和方法）的可见性和访问权限。

Scala 访问修饰符基本和 Java 的一样，分别有：private，protected，public。

如果没有指定访问修饰符，默认情况下，Scala 对象的访问级别都是 public。

Scala 中的 private 限定符，比 Java 更严格，在嵌套类情况下，外层类甚至不能访问被嵌套类的私有成员。


## 私有(Private)成员

用 private 关键字修饰，带有此标记的成员仅在包含了成员定义的类或对象内部可见，同样的规则还适用内部类。


## 实例

(new Inner).f( ) 访问不合法是因为 f 在 Inner 中被声明为 private，而访问不在类 Inner 之内。

但在 InnerMost 里访问 f 就没有问题的，因为这个访问包含在 Inner 类之内。

Java 中允许这两种访问，因为它允许外部类访问内部类的私有成员。


## 保护(Protected)成员

在 scala 中，对保护（Protected）成员的访问比 java 更严格一些。因为它只允许保护成员在定义了该成员的的类的子类中被访问。而在java中，用 protected关键字修饰的成员，除了定义了该成员的类的子类可以访问，同一个包里的其他类也可以进行访问。


## 实例

上例中，Sub 类对 f 的访问没有问题，因为 f 在 Super 中被声明为 protected，而 Sub 是 Super 的子类。相反，Other 对 f 的访问不被允许，因为 other 没有继承自 Super。而后者在 java 里同样被认可，因为 Other 与 Sub 在同一包里。


## 公共(Public)成员

Scala 中，如果没有指定任何的修饰符，则默认为 public。这样的成员在任何地方都可以被访问。


## 实例


## 包级私有访问（Package-Private）

Scala还支持包级私有访问修饰符，用于限制成员只能在特定包内访问。可以通过将private关键字后跟一个包名来实现。格式为:

```text
private[x]

或

protected[x]
```

这里的 x 指代某个所属的包、类或单例对象。

如果写成 private[x]，读作 "这个成员除了对 […] 中的类或 […] 中的包中的类及它们的伴生对像可见外，对其它所有类都是 private"。

这种技巧在横跨了若干包的大型项目中非常有用，它允许你定义一些在你项目的若干子包中可见但对于项目外部的客户却始终不可见的东西。


## 实例

上述例子中，类 Navigator 被标记为 private[bobsrockets] 就是说这个类对包含在 bobsrockets 包里的所有的类和对象可见。

比如说，从 Vehicle 对象里对 Navigator 的访问是被允许的，因为对象 Vehicle 包含在包 launch 中，而 launch 包在 bobsrockets 中，相反，所有在包 bobsrockets 之外的代码都不能访问类 Navigator。


## 伴生对象和伴生类

在 Scala 中，伴生对象和伴生类可以互相访问对方的私有成员。伴生对象和伴生类是同名且在同一文件中的类和对象。


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Scala 访问修饰符` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
