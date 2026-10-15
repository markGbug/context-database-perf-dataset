# Ruby：Ruby 哈希（Hash）

- 来源：[Ruby 哈希（Hash）](https://www.runoob.com/ruby/ruby-hash.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：练习笔记
- 章节序号：3731

## 本章内容

哈希（Hash）是类似 "key" => "value" 这样的键值对集合。哈希类似于一个数组，只不过它的索引不局限于使用数字。

Hash 的索引（或者叫"键"）几乎可以是任何对象。

Hash 虽然和数组类似，但却有一个很重要的区别：Hash 的元素没有特定的顺序。 如果顺序很重要的话就要使用数组了。


## 创建哈希

与数组一样，有各种不同的方式来创建哈希。您可以通过 new 类方法创建一个空的哈希：

```text
months = Hash.new
```

您也可以使用 new 创建带有默认值的哈希，不带默认值的哈希是 nil：

```text
months = Hash.new( "month" )

或

months = Hash.new "month"
```

当您访问带有默认值的哈希中的任意键时，如果键或值不存在，访问哈希将返回默认值：


## 实例

```text
#!/usr/bin/ruby

months = Hash.new( "month" )

puts "#{months[0]}"
puts "#{months[72]}"
```

以上实例运行输出结果为：

```text
month
month
```


## 实例

```text
#!/usr/bin/ruby

H = Hash["a" => 100, "b" => 200]

puts "#{H['a']}"
puts "#{H['b']}"
```

以上实例运行输出结果为：

```text
100
200
```

您可以使用任何的 Ruby 对象作为键或值，甚至可以使用数组，如下实例所示：

```text
[1,"jan"] => "January"
```


## 哈希内置方法

如果需要调用 Hash 方法，需要先实例化一个 Hash 对象。下面是创建 Hash 对象实例的方式：

```text
Hash[[key =>|, value]* ] or

Hash.new [or] Hash.new(obj) [or]

Hash.new { |hash, key| block }
```

这将返回一个使用给定对象进行填充的新的哈希。现在，使用创建的对象，我们可以调用任意可用的方法。例如：


## 实例

```text
#!/usr/bin/ruby

$, = ", "
months = Hash.new( "month" )

months = {"1" => "January", "2" => "February"}

keys = months.keys

puts "#{keys}"
```

以上实例运行输出结果为：

```text
["1", "2"]
```

下面是公共的哈希方法（假设 hash 是一个 Hash 对象）：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ruby 哈希（Hash）` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
