# Swift：Swift 字符串

- 来源：[Swift 字符串](https://www.runoob.com/swift/swift-strings.html)
- 分类：移动开发
- 技术：Swift
- 笔记类型：练习笔记
- 章节序号：3418

## 本章内容

字符串（String）是一系列字符的有序集合，是 Swift 里使用频率最高的类型之一。

Swift 的字符串基于 Unicode 构建，中文、emoji 这类非 ASCII 文本都能自然处理。

本篇讲字符串的创建、索引、常用方法、多行写法、Unicode 视图与比较；组成字符串的字符本身，见《Swift 字符》。


## 创建、拼接与插值

字符串可以用字面量创建，也可以用 String() 初始化；拼接用 + 或 +=，把变量塞进字符串则用 \(...) 插值。


## 实例

运行结果：

```text
Hello, World!
Hello, World!
菜鸟教程：http://www.runoob.com
Runoob 教程
20 乘于 100 等于 2000
```

空字符串可以用 "" 或 String() 创建，判断是否为空用 isEmpty，它比比较长度更直观。


## 实例

运行结果：

```text
emptyA 是空的：true
emptyB 是空的：true
```

插值里的表达式可以是任意合法 Swift 表达式，也可以嵌套调用，但不要为了炫技把复杂逻辑写进插值，可读性会变差。


## String.Index 与索引操作

Swift 的字符串不能用整数下标，因为不同字符占用的存储长度不一样，所以要用 String.Index 来定位。

常用的入口是 startIndex、endIndex，以及 index(_:offsetBy:)、index(after:)、index(before:)。


## 实例

运行结果：

```text
第 4 个字符：.
下标 4 到 10 的子串：runoob
两个下标的距离：6
startIndex 处：w
往后一格：w
endIndex 前一个：m
```

注意：endIndex 指向最后一个字符的后面，它本身不是有效字符位置，所以要用 index(before:) 才能取到最后一个字符。

下标只能来自同一个字符串。用别的字符串算出来的下标去索引，运行时可能崩溃，这是 String.Index 与整数下标最大的不同。


## 常用方法

下表列出字符串最常用的一批成员，其中 prefix、suffix、split 返回的是 Substring 或 [Substring]，需要时可以转成 String。


## 实例

运行结果：

```text
长度：14
isEmpty：false
prefix(3)：www
suffix(3)：com
contains("runoob")：true
hasPrefix("www")：true
hasSuffix("com")：true
split 结果个数：3
第一个：Runoob
joined 还原：Runoob | RUNOOB | 菜鸟教程
替换后：www.RUNOOB.com
```

要注意 hasPrefix(_:) 和 hasSuffix(_:) 只接受一个无标签参数，老教程里的 hasPrefix(prefix:) 写法早已失效。

split(separator:) 默认会丢弃空子串，连续的分隔符不会产生空元素；需要保留时传 omittingEmptySubsequences: false。


## 实例

运行结果：

```text
Substring
String
```


## 多行字符串与 trimmingCharacters

三引号可以写多行字符串，闭合三引号的缩进以内的空白不会被保留；如果字符串前后有多余的空白或换行，可以用 trimmingCharacters(in:) 清掉。


## 实例

运行结果：

```text
原始长度：22
裁剪后：|Runoob
www.runoob.com|
```

多行字符串的缩进规则是：以闭合三引号那一行的缩进为基准，每一行都会去掉这段共同缩进，因此代码排版和字符串内容互不干扰。

trimmingCharacters(in:) 常用的参数还有 .whitespaces（只去空格和制表符）和 .newlines（只去换行）。


## Unicode 视图

同一个字符串可以按三种视图查看底层的编码：utf8 是 UTF-8 字节序列，utf16 是 UTF-16 码元序列，unicodeScalars 是 Unicode 标量序列。

三种视图的元素个数往往不一样，因为一个字符可能对应多个标量、一个标量又可能对应多个字节。


## 实例

运行结果：

```text
UTF-8：[232, 143, 156, 233, 184, 159]
UTF-16：[33756, 40479]
Unicode 标量值：[33756, 40479]
```

注意：UTF-8 是变长编码，一个汉字占 3 个字节，所以「菜鸟」的 UTF-8 有 6 个元素，而 UTF-16 和 Unicode 标量都只有 2 个。不要把 utf8.count 当成字符个数。

要遍历用户看到的字符，用 for c in str 或 Array(str) 即可，它们走的都是 Character 视图；只有在处理二进制协议、文件格式这类场景才需要下沉到 utf8 或 utf16。


## 字符串比较

Swift 用 ==、!= 判断字符串是否相等，用 <、> 做字典序比较。

比较基于 Unicode 规范等价：写法不同但视觉相同的字符会被视为相等。


## 实例

运行结果：

```text
cmpA == cmpB：false
cmpA != cmpB：true
cmpA < cmpB：true
```

下面这个例子能说明「规范等价」的含义：一个用预组合字符，一个用字母加组合音标，底层码点完全不同，但比较结果是相等的。


## 实例

运行结果：

```text
两种写法相等：true
cafe1 的 count：4
cafe2 的 count：4
```

正因为 Swift 的相等判断走的是规范等价，用 == 比较用户输入和预置文本才是可靠的，不需要自己做 Unicode 归一化。


## 常见问题

下面几个问题在初学 Swift 字符串时出现频率最高。


### 为什么不能用 str[0] 取字符

Swift 的字符长度不固定，一个 Character 可能占多个字节，用整数下标无法在常数时间内定位，必须用 String.Index。


### count 和 utf8.count 为什么不一样

count 数的是扩展字素簇，也就是人眼看到的字符；utf8.count 数的是字节。一个汉字在 count 里是 1，在 utf8.count 里是 3。


### hasPrefix(prefix:) 报错怎么办

现代写法是 hasPrefix(_:)，直接把要检查的前缀字符串传进去即可，不要写参数标签。


### prefix 返回的为什么不是 String

它返回 Substring，与原字符串共享底层存储，这样切片不必复制；需要一份独立字符串时用 String(...) 包一层。


### 字符串是值类型还是引用类型

是值类型。赋值和传参时语义上都会复制一份，实际由编译器在底层共享存储、写入时才复制，使用上和 Int 一样安全。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Swift 字符串` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
