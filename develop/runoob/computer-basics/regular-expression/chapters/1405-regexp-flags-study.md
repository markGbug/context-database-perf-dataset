# 正则表达式：正则表达式 - 修饰符（标记）

- 来源：[正则表达式 - 修饰符](https://www.runoob.com/regexp/regexp-flags.html)
- 分类：计算机基础
- 技术：正则表达式
- 笔记类型：学习笔记
- 章节序号：1405

## 本章内容

正则表达式修饰符（也称为模式修饰符或标记）是用于改变正则表达式匹配行为的特殊指令。

标记也称为修饰符，正则表达式的标记用于指定额外的匹配策略。

标记不写在正则表达式里，标记位于表达式之外，格式如下：

```text
/pattern/flags
```


## 常用修饰符

下表列出了正则表达式常用的修饰符：


### 1. i (ignore case) - 忽略大小写

- 使匹配不区分大小写
- 示例：/abc/i 可以匹配 "abc", "Abc", "ABC" 等
- 支持语言：几乎所有正则表达式实现（JavaScript、PHP、Python等）


### 2. g (global) - 全局匹配

- 查找所有匹配项，而不是在第一个匹配后停止
- 示例：在字符串 "ababab" 中，/ab/g 会匹配所有三个 "ab"
- 支持语言：JavaScript、PHP等


### 3. m (multiline) - 多行模式

- 改变 ^ 和 $ 的行为，使其匹配每行的开头和结尾，而不仅是整个字符串的开头和结尾
- 示例：在多行字符串中，/^abc/m 会匹配每行开头的 "abc"
- 支持语言：JavaScript、PHP、Python、Perl等


### 4. s (single line/dotall) - 单行模式

- 使点号 . 匹配包括换行符在内的所有字符
- 在JavaScript中称为"dotall"模式，使用 /s 修饰符
- 示例：/a.b/s 可以匹配 "a\nb"
- 支持语言：PHP、Perl、Python(作为re.DOTALL)、JavaScript(ES2018+)


### 5. u (unicode) - Unicode模式

- 启用完整的Unicode支持
- 正确处理UTF-16代理对和Unicode字符属性
- 示例：/\p{Script=Greek}/u 可以匹配希腊字母
- 支持语言：JavaScript、PHP等


### 6. y (sticky) - 粘性匹配

- 从目标字符串的当前位置开始匹配（使用lastIndex属性）
- 类似于^锚点，但针对的是匹配的起始位置
- 示例：在JavaScript中，/a/y 会从lastIndex开始匹配 "a"
- 支持语言：JavaScript


### 7. x (extended) - 扩展模式

- 忽略模式中的空白和注释，使正则表达式更易读
- 示例：在PHP中，/a b c/x 等同于 /abc/
- 支持语言：PHP、Perl、Python(作为re.VERBOSE)


### g 修饰符

g 修饰符可以查找字符串中所有的匹配项：


## 实例

在字符串中查找 "runoob":

```javascript
var str="Google runoob taobao runoob";
var n1=str.match(/runoob/);   // 查找第一次匹配项
var n2=str.match(/runoob/g);  // 查找所有匹配项
```


### i 修饰符

i 修饰符为不区分大小写匹配，实例如下：


## 实例

在字符串中查找 "runoob":

```javascript
var str="Google runoob taobao RUNoob";
var n1=str.match(/runoob/g);   // 区分大小写
var n2=str.match(/runoob/gi);  // 不区分大小写
```


### m 修饰符

m 修饰符可以使 ^ 和 $ 匹配一段文本中每行的开始和结束位置。

g 只匹配第一行，添加 m 之后实现多行。

以下实例字符串中使用 \n 来换行：


## 实例

在字符串中查找 "runoob":

```javascript
var str="runoobgoogle\ntaobao\nrunoobweibo";
var n1=str.match(/^runoob/g);   // 匹配一个
var n2=str.match(/^runoob/gm);  // 多行匹配
```


### s 修饰符

默认情况下的圆点 . 是 匹配除换行符 \n 之外的任何字符，加上 s 之后, . 中包含换行符 \n。

s 修饰符实例如下：


## 实例

在字符串中查找:

```javascript
var str="google\nrunoob\ntaobao";
var n1=str.match(/google./);   // 没有使用 s，无法匹配\n
var n2=str.match(/runoob./s);  // 使用 s，匹配\n
```


## 扩展说明

语言特定修饰符补充表：

修饰符组合示例表：

内联修饰符表（PCRE/Perl风格）：

注意：不同语言对修饰符的实现可能存在差异，建议使用时参考具体语言的文档。


## 复习重点

- 能说明 `正则表达式 - 修饰符` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
