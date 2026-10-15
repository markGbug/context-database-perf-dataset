# Swift：Swift 字符

- 来源：[Swift 字符](https://www.runoob.com/swift/swift-characters.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：练习笔记
- 章节序号：3419

## 本章内容

字符（Character）表示人眼看到的一个字符，是字符串的组成单位。

Swift 的 Character 既不是字节，也不是 Unicode 码点，而是一个扩展字素簇，这是它和 C 系语言里的 char 最大的区别。

本篇讲 Character 的含义、扩展字素簇语义、与 String 的互转，以及字面量和类型标注的区别；字符串本身的用法见《Swift 字符串》。


## Character 是什么

Character 表示单个扩展字素簇，必须用双引号赋值，并且里面只能放一个字符。

声明时必须写类型标注，否则编译器会把双引号里的内容推断成 String，而不是 Character。


## 实例

运行结果：

```text
char1 的值为 A
char2 的值为 牛
```

注意：Character 不能是空字符串，也不能塞进多个字符。写 let c: Character = "AB" 或 let c: Character = "" 都会报 cannot convert value of type 'String' to specified type 'Character'。

一个字符串由若干 Character 组成，用 for-in 逐个遍历时，遍历出来的每个元素都是 Character。


## 实例

运行结果：

```text
R
u
n
o
o
b
```

这里输出的每个 ch 都是 Character，而不是 String，所以能直接参与 Character 的运算和比较。


## 扩展字素簇语义

Swift 里「一个字符」指的是一个扩展字素簇（extended grapheme cluster），也就是人眼看到的一个字符，而不是底层的字节或码元。

带音标的字母、肤色修饰的 emoji、由多个 emoji 组合成的家庭符号，都算一个 Character。


## 实例

运行结果：

```text
precomposed 的 count：1
combined 的 count：1
两者相等：true
family 的 count：1
thumbsUp 的 count：1
```

这些例子的共同点是：底层的 Unicode 标量数量不止一个，但都属于同一个扩展字素簇，所以 count 都是 1。

扩展字素簇的边界规则由 Unicode 标准定义，Swift 直接采用了它，因此不同语言里「一个字符」的直觉在 Swift 中基本都能对上。


## Character 与 String 的互转

Character 和 String 之间可以互相转换，最常用的几种写法如下。


## 实例

运行结果：

```text
["R", "u", "n", "o", "o", "b"]
6
R
String
```

反过来，Character 也可以用 append 追加到字符串末尾。


## 实例

运行结果：

```text
Hello !
```

字符数组拼回字符串时直接写 String(chars)；如果中间想加分隔符，需要先把每个 Character 转成 String，再用 joined(separator:)，因为 [Character] 本身没有这个方法。


## 实例

运行结果：

```text
Runoob
R-u-n-o-o-b
```


## Character 字面量与类型标注

双引号里的内容默认是 String，即使它只有一个字符也一样；只有显式标注类型或用 as Character 转换，才会得到 Character。


## 实例

运行结果：

```text
String
Character
Character
```

三行代码看起来一样，类型却不同：inferred 是 String，另外两个是 Character。需要 Character 时，优先用类型标注，它比 as 转换更直观。

从变量转换也一样，Character(someString) 可以把一个内容恰好为单字符的 String 转成 Character，但如果字符串为空或长度大于 1，程序会在运行时终止，所以转换前要确认内容。


## 常见问题

下面是初学者使用 Character 时最常遇到的几个问题。


### 为什么 "👨‍👩‍👧‍👦".count 是 1

这个家庭 emoji 由四个成员 emoji 和三个零宽连接符组成，底层有 7 个 Unicode 标量、25 个 UTF-8 字节，但它们属于同一个扩展字素簇，人眼看到的就是一个符号，所以 count 是 1。


### Character 能不能直接和 String 比较

不能。Character 和 String 之间没有 == 重载，c == s（s 是 String 变量）会报 binary operator '==' cannot be applied to operands of type 'Character' and 'String'。但 c == "A" 是合法的，因为字面量 "A" 会被推断成 Character；要比较 String 变量，先用 String(c) 转换。


## 实例

运行结果：

```text
c == "A"：true
String(c) == s：true
c == Character(s)：true
```


### 怎么把字符串拆成字符数组

用 Array(str) 得到一个 [Character]，之后就能用数组下标、map、filter 等所有集合操作；只想遍历而不用保存时，直接 for c in str 更省事。


### Character 能放空字符串吗

不能，空字符串和多字符字符串都会报 cannot convert value of type 'String' to specified type 'Character'。需要表示「没有字符」时，用可选类型 Character? 并赋 nil。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Swift 字符` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
