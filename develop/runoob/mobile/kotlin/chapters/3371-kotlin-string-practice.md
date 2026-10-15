# Kotlin：Kotlin 字符串与正则

- 来源：[Kotlin 字符串与正则](https://www.runoob.com/kotlin/kotlin-string.html)
- 分类：移动开发
- 技术：Kotlin
- 笔记类型：练习笔记
- 章节序号：3371

## 本章内容

字符串是编程中最常用的数据类型，用来表示文本。

Kotlin 的 String 类提供了丰富的查找、截取、替换方法，还支持原始字符串和字符串模板，写起来比 Java 简洁很多。

本篇先介绍字符串本身，再介绍正则表达式 Regex 的完整用法。


## 字符串基础与不可变性

字符串用双引号包裹，类型是 String。

String 是不可变的（immutable）：一旦创建，内容就不能再改变。

所有看起来像"修改"的方法，例如 uppercase()、replace()，实际上都返回一个新的字符串，原字符串保持不变。


## 实例

```text
Runoob
RUNOOB
R
6
Runoob
```

比较字符串内容要用 ==，它比较的是值；=== 比较的是引用，不要用来判断字符串是否相等。


## 实例

```text
true
true
false
```

注意：字符串不可变意味着拼接、替换都会产生新对象。在循环里反复拼接字符串时，应改用 StringBuilder，否则会产生大量临时对象。


## 转义字符串与原始字符串

Kotlin 有两种字符串字面量：转义字符串和原始字符串。

转义字符串用一对双引号包裹，支持 \n、\t 等转义序列。

原始字符串用三个双引号包裹，内容原样保留，反斜杠和引号都不需要转义，适合写路径、JSON 和正则。


## 实例

```text
第一行
第二行
第一行
第二行
C:\Users\runoob\kotlin
{"site": "www.runoob.com"}
$9.99
```

提示：原始字符串中唯一需要注意的字符是 $，它仍会触发字符串模板。需要输出字面量美元符号时，写成 ${'$'}。


## trimIndent 与 trimMargin

用原始字符串写多行文本时，代码缩进会被一起保留，看起来会有多余的空格。

trimIndent() 会删除所有行共同的缩进，以及首尾的空行。

trimMargin() 则按边界前缀（默认是竖线）裁剪每一行，适合需要保留部分缩进的场景。


## 实例

```text
Runoob
www.runoob.com
RUNOOB
Runoob
www.runoob.com
RUNOOB
Runoob
RUNOOB
```

trimIndent() 计算公共缩进时会忽略空行，所以中间插入空行不影响结果。

trimMargin() 只删除边界前缀之前的内容，前缀之后的部分保持原样，因此可以灵活控制每行的起始位置。


## 字符串模板

字符串模板允许把变量或表达式直接嵌入字符串，用 $ 开头。

简单的变量名用 $name，表达式或带点的调用用 ${...}。


## 实例

```text
站点：Runoob
Runoob 已上线 10 年
Runoob 长度是 6
明年是第 11 年
大写：RUNOOB
价格：$9.99
```

注意：当变量名后面紧跟其他字母时，必须用 ${name} 形式，否则编译器会把后续字符当作变量名的一部分。例如 "$siteNameSuffix" 会去找名为 siteNameSuffix 的变量。


## 常用方法

下表列出了日常开发中最常用的字符串方法。

下面的例子演示了这些方法的具体结果。


## 实例

```text
17
Runoob Kotlin
runoob kotlin
RUNOOB KOTLIN
false
true
true
Runoob
Runoob RUNOOB
7
007
ababab
[a, b, c]
true
true
```

split() 还可以同时指定多个分隔符，或者直接传入一个正则表达式。


## 实例

```text
[a, b, c]
[a, b, c]
[a, b, c,d]
```


## 字符串格式化

需要对齐、补零或控制小数位数时，可以使用格式化函数。

在 JVM 平台上，Kotlin 提供了 String.format() 静态方法和字符串的 format() 扩展函数，语法与 Java 的格式化字符串一致。


## 实例

```text
Runoob 的得分是 95.50
站点：Runoob，得分：96
runoob    |
00042
ff
```

下表列出了最常用的占位符。

注意：String.format 依赖 JVM，在 Kotlin/JS 和 Kotlin/Native 上不可用。跨平台代码请改用字符串模板或自己实现补位逻辑。


## 正则表达式 Regex

正则表达式用来描述一类文本的模式，常用于校验、提取和替换。

Kotlin 用 Regex 类封装正则功能，创建方式是调用 Regex 构造函数或字符串的 toRegex() 扩展函数。

推荐用原始字符串写正则，这样反斜杠只需要写一次。


## 实例

```text
true
false
true
true
```


### find 与 findAll

find() 返回第一个匹配结果，findAll() 返回所有匹配结果的序列。


## 实例

```text
2026
7..10
[2026, 9, 8]
[2026, 9]
```

MatchResult 的 value 是匹配到的文本，range 是它在原字符串中的下标区间。


### replace 与 split

replace() 可以把所有匹配替换成指定内容，split() 可以按匹配切分字符串。


## 实例

```text
a#b#c#
a<1>b<2>c<3>
[a, b, c]
a#b2
```


### 捕获组

用圆括号可以把正则的一部分括成捕获组，匹配后可以单独取出每一组的内容。

groupValues[0] 是整体匹配，之后依次是第 1、2、3 个捕获组。


## 实例

```text
[2026-09-08, 2026, 09, 08]
2026
09
08
2026
09
```

matchEntire() 和 matches() 都要求整个字符串匹配，区别是前者返回 MatchResult?，后者只返回 Boolean。


### 正则选项

构造 Regex 时可以传入 RegexOption 来改变匹配行为，例如忽略大小写、多行模式。


## 实例

```text
true
true
[123, 456]
```

提示：如果正则中需要匹配字符 .、*、+、?、( 等本身，必须加反斜杠转义，或者用 Regex.escape() 把普通字符串转成安全的正则片段。


## 后续章节

- 常见问题
- 为什么修改字符串后原值没变
- 原始字符串里怎么输出 $
- 字符串拼接用 + 还是模板
- matches 和 find 有什么区别
- 正则里为什么要用三个引号

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Kotlin 字符串与正则` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
