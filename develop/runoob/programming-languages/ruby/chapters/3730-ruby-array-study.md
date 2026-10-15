# Ruby：Ruby 数组（Array）

- 来源：[Ruby 数组（Array）](https://www.runoob.com/ruby/ruby-array.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：学习笔记
- 章节序号：3730

## 本章内容

Ruby 数组是任何对象的有序整数索引集合。数组中的每个元素都与一个索引相关，并可通过索引进行获取。

数组的索引从 0 开始，这与 C 或 Java 中一样。一个负数的索相对于数组的末尾计数的，也就是说，索引为 -1 表示数组的最后一个元素，-2 表示数组中的倒数第二个元素，依此类推。

Ruby 数组可存储诸如 String、 Integer、 Fixnum、 Hash、 Symbol 等对象，甚至可以是其他 Array 对象。

Ruby 数组不需要指定大小，当向数组添加元素时，Ruby 数组会自动增长。


## 创建数组

有多种方式创建或初始化数组。一种方式是通过 new 类方法：

```text
names = Array.new
```

您可以在创建数组的同时设置数组的大小：

```text
names = Array.new(20)
```

数组 names 的大小或长度为 20 个元素。您可以使用 size 或 length 方法返回数组的大小：


## 实例

```text
#!/usr/bin/ruby

names = Array.new(20)
puts names.size  # 返回 20
puts names.length # 返回 20
```

以上实例运行输出结果为：

```text
20
20
```

您可以给数组中的每个元素赋值，如下所示：


## 实例

```text
#!/usr/bin/ruby

names = Array.new(4, "mac")

puts "#{names}"
```

以上实例运行输出结果为：

```text
["mac", "mac", "mac", "mac"]
```

您也可以使用带有 new 的块，每个元素使用块中的计算结果来填充：


## 实例

```text
#!/usr/bin/ruby

nums = Array.new(10) { |e| e = e * 2 }

puts "#{nums}"
```

以上实例运行输出结果为：

```text
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]
```

数组还有另一种方法，[]，如下所示：

```text
nums = Array.[](1, 2, 3, 4,5)
```

数组创建的另一种形式如下所示：

```text
nums = Array[1, 2, 3, 4,5]
```

在 Ruby 核心模块中可以有一个只接收单个参数的 Array 方法，该方法使用一个范围作为参数来创建一个数字数组：


## 实例

```text
#!/usr/bin/ruby

digits = Array(0..9)

puts "#{digits}"
```

以上实例运行输出结果为：

```text
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```


## 数组内建方法

我们需要有一个 Array 对象的实例来调用 Array 方法。下面是创建 Array 对象实例的方式：

```text
Array.[](...) [or] Array[...] [or] [...]
```

这将返回一个使用给定对象进行填充的新数组。现在，使用创建的对象，我们可以调用任意可用的方法。例如：


## 实例

```text
#!/usr/bin/ruby

digits = Array(0..9)

num = digits.at(6)

puts "#{num}"
```

以上实例运行输出结果为：

```text
6
```

下面是公共的数组方法（假设 array 是一个 Array 对象）：


## 数组 pack 指令

下表列出了方法 Array#pack 的压缩指令。


### 实例

尝试下面的实例，压缩各种数据。


## 实例

```text
a = [ "a", "b", "c" ]
n = [ 65, 66, 67 ]
puts a.pack("A3A3A3")   #=> "a  b  c  "
puts a.pack("a3a3a3")   #=> "a\000\000b\000\000c\000\000"
puts n.pack("ccc")      #=> "ABC"
```

以上实例运行输出结果为：

```text
a  b  c
abc
ABC
```


## 复习重点

- 能说明 `Ruby 数组（Array）` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
