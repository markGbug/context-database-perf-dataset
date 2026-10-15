# Kotlin：Kotlin 空安全

- 来源：[Kotlin 空安全](https://www.runoob.com/kotlin/kotlin-null-safety.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：学习笔记
- 章节序号：3392

## 本章内容

空安全（null safety）是 Kotlin 最核心的语言特性，它在类型系统层面把"可能为 null"和"一定不为 null"区分开。

只要编译器判断某个值可能为 null，就必须显式处理，否则代码无法通过编译，大量空指针异常因此被提前到编译期发现。


## 可空类型与非空类型

Kotlin 的类型默认都不可为 null，只有加上问号 ? 才表示可空。

非空类型可以放心调用成员，可空类型必须先做判空处理，编译器不会替你假设它不为 null。


## 实例

运行结果：

```text
6
14
null
```

注意：可空类型和非空类型在运行时是同一个 JVM 类型，区别只存在于编译期的类型标记。这也意味着绕过编译器（比如 Java 互操作或反射）依然可能产生 null。


## 安全调用 ?.

安全调用 ?. 表示"如果接收者不为 null 才调用，否则整个表达式返回 null"。

它可以链式书写，链条上任何一环为 null，后续调用都会跳过，最终结果是 null。


## 实例

运行结果：

```text
北京
null
null
```

安全调用同样可以用于函数调用，例如 site?.trim()，接收者为 null 时不会执行函数，直接返回 null。


## Elvis 运算符 ?:

Elvis 运算符 ?: 表示"左边为 null 时取右边的值"，用来提供兜底方案。

它右侧是惰性求值的，只有左边确实为 null 时才会计算，因此可以安全地写 throw 或 return。


## 实例

运行结果：

```text
游客
8080
端口不合法：abc
```

Elvis 右侧也可以直接写 return，用于函数提前退出。


## 实例

运行结果：

```text
欢迎 Runoob
名字不能为空
```


## 非空断言 !!

双感叹号 !! 是"我确定它不为 null"的断言。

一旦实际值为 null，程序会立即抛出 NullPointerException，因此它只是把编译期的检查推迟到了运行时。


## 实例

运行结果：

```text
6
java.lang.NullPointerException
```

建议：能用 ?. 和 ?: 解决的问题就不要用 !!。!! 应该只出现在确实已经完成判空、但编译器无法感知的场景。


## 安全调用与 let

?. 只能返回 null 或调用结果，如果需要对非空值做一段操作，惯用法是配合 let。

a?.let { } 表示 a 非空时执行 lambda，参数 it 就是智能转换后的非空值。


## 实例

运行结果：

```text
发送邮件到 runoob@www.runoob.com
长度：21
```

智能转换（smart cast）是 Kotlin 的另一项能力：一旦在分支里完成判空，编译器就把它当作非空类型，无需再写 !!。


## 安全转换 as?

强制转换 as 在类型不匹配时会抛 ClassCastException。

安全转换 as? 则在失败时返回 null，适合处理类型不确定的输入。


## 实例

运行结果：

```text
String=RUNOOB, Int=null
String=null, Int=42
String=null, Int=null
```

与之配套的还有 is 判断，判断成功后同样会触发智能转换。


## 实例

运行结果：

```text
6
-1
```


## 平台类型与 Java 互操作

Kotlin 调用没有空安全注解的 Java 方法时，返回类型会变成平台类型，写作 String!。

平台类型的意思是"编译器不知道它是否可能为 null"，因此既允许赋给非空类型，也允许赋给可空类型。

先看 Java 侧的代码。


## 实例

Kotlin 侧把返回值赋给非空类型时不会报错，但运行时会触发空检查。


## 实例

运行结果：

```text
捕获到异常：java.lang.NullPointerException
异常信息：getName(...) must not be null
```

风险提示：平台类型是空安全体系的漏洞所在。处理 Java 返回值时，除非有 @NotNull 注解或明确的文档保证，否则一律当作可空类型处理。

推荐的写法是显式声明为可空类型，再用 Elvis 或安全调用兜底。


## 实例

运行结果：

```text
站点名称：未命名
名称长度：0
```


## lateinit 延迟初始化

有时属性无法在构造阶段确定值，比如由框架注入或在 onCreate 中赋值，这时可以用 lateinit。

它告诉编译器"我保证在第一次访问前完成赋值"，如果访问时还没赋值，会抛出 UninitializedPropertyAccessException。


## 实例

运行结果：

```text
站点尚未初始化
站点：www.runoob.com
```

lateinit 常和 by lazy 一起比较，两者解决的是不同问题。


## 集合与泛型的可空性

集合本身是否可空，和集合元素是否可空，是两个独立的维度，可以自由组合。

List<String> 表示非空列表装非空元素，List<String?> 表示非空列表装可空元素，List<String>? 表示可空列表装非空元素。


## 实例

运行结果：

```text
2
null
3
null
null
0
[Runoob, RUNOOB]
```

常见的"取不到就返回 null"的 API 还有 getOrNull、firstOrNull、lastOrNull、singleOrNull，它们比抛异常的版本更适合空安全风格。


## 常见问题

用了空安全，Kotlin 程序就不会再有 NullPointerException 了吗？

不是。平台类型、!!、lateinit 未初始化、反射和泛型擦除这几条路径依然可能产生 NPE，只是它们都属于可以主动避免的少数情况。

什么时候该用 !!，什么时候该用 ?:？

逻辑上可能为 null 时用 ?: 给默认值或抛业务异常；只有在已经通过其他方式保证非空、但编译器无法推断时才用 !!。

可空类型能用 == 和 null 比较吗？

可以，x == null 是合法的，也是最直观的判空写法。equals 的翻译规则专门处理了 null 的情况。

lateinit 为什么不能修饰基本类型？

因为基本类型在 JVM 上有默认值（如 Int 默认 0），无法区分"未初始化"和"值为 0"，所以只能用引用类型。


## 复习重点

- 能说明 `Kotlin 空安全` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
