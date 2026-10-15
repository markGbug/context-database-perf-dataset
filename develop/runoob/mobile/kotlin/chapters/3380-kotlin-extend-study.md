# Kotlin：Kotlin 继承

- 来源：[Kotlin 继承](https://www.runoob.com/kotlin/kotlin-extend.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3380

## 本章内容

继承让子类复用父类的属性和方法，并在需要时改写它们的行为。

Kotlin 的继承比 Java 更保守：类和方法默认都是 final 的，必须显式打开才能被继承或重写。


## Any 与通用方法

Kotlin 中所有类都有一个共同的超类 Any，没有显式写父类的类都默认继承它。

Any 声明了三个方法：equals()、hashCode() 和 toString()，它们的默认实现都可以被子类重写。


## 实例

输出结果：

```text
Site(name=RUNOOB, url=www.runoob.com)
a == b：true
a === b：false
哈希码相同：true
```

== 调用的是 equals()，比较内容；=== 比较引用，判断是不是同一个对象。

提示：只重写 equals 而不重写 hashCode，会让对象在 HashSet、HashMap 里表现异常。两者要成对出现。


## open 关键字

Kotlin 的类默认是 final 的，不能被继承；想被继承必须加 open。

类里的成员同样默认是 final 的，想被重写也要单独加 open。


## 实例

输出结果：

```text
汪汪
旺财 在吃东西
dog 是 Animal：true
```

如果写成 class Cat : Animal("咪咪") 而 Animal 没有 open，编译器会直接报错。


## 子类有主构造器时的基类初始化

子类有主构造器时，父类必须在子类的类头里就地初始化，写法是父类名加括号。

父类的初始化块先于子类的初始化块执行，这一点和大多数面向对象语言一致。


## 实例

输出结果：

```text
基类 init：RUNOOB
子类 init：www.runoob.com
站点：RUNOOB，地址：www.runoob.com
```

子类构造器执行时，父类的属性已经初始化完毕，所以 super.show() 能安全读到 name。


## 子类无主构造器时的 super 调用

子类没有主构造器时，父类要在每个次构造器里用 super(...) 初始化，或者委托给另一个已经初始化父类的次构造器。

下面的例子让父类只有次构造器，子类也全部使用次构造器。


## 实例

输出结果：

```text
Person 次构造器：小明
Person 次构造器（带年龄）：小明，18
Student 次构造器（带年龄）：小明，18
角色：学生
```

无论用哪种方式，父类构造函数一定先执行完，子类构造器的代码体才会开始。


## 方法重写 override

子类重写父类的成员必须写 override 关键字，编译器会检查被重写的成员确实存在且是 open 的。

重写后的成员默认仍然是 open 的，如果不希望再被重写，要加 final。


## 实例

输出结果：

```text
Leaf.foo
Middle.bar
```

foo() 被 Leaf 再次重写，bar() 则停在 Middle，这就是 final override 的作用。


## 属性重写

属性也可以重写，规则是：父类的 val 属性可以被子类的 val 或 var 重写，但父类的 var 不能被 val 重写。

原因很直观：val 只承诺提供 getter，var 额外提供 setter，能力只能增加不能减少。


## 实例

输出结果：

```text
Runoob
www.runoob.com
https://www.runoob.com
```

反过来把父类的 var 用子类的 val 重写，编译器会报「Var-property cannot be overridden by val-property」。


## super 消歧

当一个类同时实现多个接口，而这些接口提供了同名成员的默认实现时，子类必须显式重写，并用 super<类型名> 指定调用哪一个。

这种写法在单继承的类之间不会出现，只出现在多接口的场景。


## 实例

输出结果：

```text
A.foo | B.foo
```

同样的规则也适用于接口中的属性，例如 super<A>.label。


## 覆盖规则与 final

把覆盖相关的规则集中在一起，写代码时对照检查。

重写时还要注意可见性不能收紧：父类成员是 public，子类不能重写成 protected 或 private。


## 常见问题

下面是继承里最容易出错的地方。


### 为什么我的类不能被继承

Kotlin 的类默认是 final 的，在 class 前加 open 即可，方法同理。


### 重写时必须写 override 吗

必须。Kotlin 用 override 显式表达意图，漏写会报「hides member of supertype」或「needs override」这类错误。


### 子类没有主构造器时怎么初始化父类

在每个次构造器上用 super(...)，或委托给另一个已经完成父类初始化的次构造器。


### val 属性能不能重写成 var

可以，反过来不行。因为 var 比 val 多一个 setter，能力增加是允许的，减少则不行。


### super 和 super<A> 有什么区别

super 用于单继承，指向唯一的父类；super<A> 用于多接口，显式指定某个父类型的实现。


## 复习重点

- 能说明 `Kotlin 继承` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
