# Ruby：Ruby 正则表达式

- 来源：[Ruby 正则表达式](https://www.runoob.com/ruby/ruby-regular-expressions.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：学习笔记
- 章节序号：3740

## 本章内容

正则表达式是一种特殊序列的字符，它通过使用有专门语法的模式来匹配或查找字符串集合。

正则表达式用事先定义好的一些特定字符、及这些特定字符的组合，组成一个"规则字符串"，这个"规则字符串"用来表达对字符串的一种过滤逻辑。


## 语法

正则表达式从字面上看是一种介于斜杠之间或介于跟在 %r 后的任意分隔符之间的模式，如下所示：

```text
/pattern/
/pattern/im    # 可以指定选项
%r!/usr/local! # 使用分隔符的正则表达式
```


## 实例

```text
#!/usr/bin/ruby

line1 = "Cats are smarter than dogs";
line2 = "Dogs also like meat";

if ( line1 =~ /Cats(.*)/ )
  puts "Line1 contains Cats"
end
if ( line2 =~ /Cats(.*)/ )
  puts "Line2 contains  Dogs"
end
```

以上实例运行输出结果为：

```text
Line1 contains Cats
```


## 正则表达式修饰符

正则表达式从字面上看可能包含一个可选的修饰符，用于控制各方面的匹配。修饰符在第二个斜杠字符后指定，如上面实例所示。下标列出了 可能的修饰符：

就像字符串通过 %Q 进行分隔一样，Ruby 允许您以 %r 作为正则表达式的开头，后面跟着任意分隔符。这在描述包含大量您不想转义的斜杠字符时非常有用。

```text
# 下面匹配单个斜杠字符，不转义
%r|/|

# Flag 字符可通过下面的语法进行匹配
%r[</(.*)>]i
```


## 正则表达式模式

除了控制字符，(+ ? . * ^ $ ( ) [ ] { } | \)，其他所有字符都匹配本身。您可以通过在控制字符前放置一个反斜杠来对控制字符进行转义。

下表列出了 Ruby 中可用的正则表达式语法。


## 正则表达式实例


## 字符


## 字符类


## 特殊字符类


## 重复


## 非贪婪重复

这会匹配最小次数的重复。


## 通过圆括号进行分组


## 反向引用

这会再次匹配之前匹配过的分组。


## 替换


## 锚

这需要指定匹配位置。


## 圆括号的特殊语法


## 搜索和替换

sub 和 gsub 及它们的替代变量 sub! 和 gsub! 是使用正则表达式时重要的字符串方法。

所有这些方法都是使用正则表达式模式执行搜索与替换操作。sub 和 sub! 替换模式的第一次出现，gsub 和 gsub! 替换模式的所有出现。

sub 和 gsub 返回一个新的字符串，保持原始的字符串不被修改，而 sub! 和 gsub! 则会修改它们调用的字符串。


## 实例

```text
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

phone = "138-3453-1111 #这是一个电话号码"

# 删除 Ruby 的注释
phone = phone.sub!(/#.*$/, "")
puts "电话号码 : #{phone}"

# 移除数字以外的其他字符
phone = phone.gsub!(/\D/, "")
puts "电话号码 : #{phone}"
```

以上实例运行输出结果为：

```text
电话号码 : 138-3453-1111
电话号码 : 13834531111
```


## 实例

```text
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

text = "rails 是 rails,  Ruby on Rails 非常好的 Ruby 框架"

# 把所有的 "rails" 改为 "Rails"
text.gsub!("rails", "Rails")

# 把所有的单词 "Rails" 都改成首字母大写
text.gsub!(/\brails\b/, "Rails")

puts "#{text}"
```

以上实例运行输出结果为：

```text
Rails 是 Rails,  Ruby on Rails 非常好的 Ruby 框架
```


## 复习重点

- 能说明 `Ruby 正则表达式` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
