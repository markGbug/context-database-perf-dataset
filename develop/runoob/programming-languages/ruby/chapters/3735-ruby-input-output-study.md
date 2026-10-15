# Ruby：Ruby 文件的输入与输出

- 来源：[Ruby 文件的输入与输出](https://www.runoob.com/ruby/ruby-input-output.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：学习笔记
- 章节序号：3735

## 本章内容

Ruby 提供了一整套 I/O 相关的方法，在内核（Kernel）模块中实现。所有的 I/O 方法派生自 IO 类。

类 IO 提供了所有基础的方法，比如 read、 write、 gets、 puts、 readline、 getc 和 printf。

本章节将讲解所有 Ruby 中可用的基础的 I/O 函数。如需了解更多的函数，请查看 Ruby 的 IO 类。


## puts 语句

在前面的章节中，您赋值给变量，然后使用 puts 语句打印输出。

puts 语句指示程序显示存储在变量中的值。这将在每行末尾添加一个新行。


## 实例

```text
#!/usr/bin/ruby

val1 = "This is variable one"
val2 = "This is variable two"
puts val1
puts val2
```

以上实例运行输出结果为：

```text
This is variable one
This is variable two
```


## gets 语句

gets 语句可用于获取来自名为 STDIN 的标准屏幕的用户输入。


### 实例

下面的代码演示了如何使用 gets 语句。该代码将提示用户输入一个值，该值将被存储在变量 val 中，最后会被打印在 STDOUT 上。


## 实例

```text
#!/usr/bin/ruby

puts "Enter a value :"
val = gets
puts val
```

以上实例运行输出结果为：

```text
Enter a value :
This is entered value
This is entered value
```


## putc 语句

与 puts 语句不同，puts 语句输出整个字符串到屏幕上，而 putc 语句可用于依次输出一个字符。


### 实例

下面代码的输出只是字符 H：


## 实例

```text
#!/usr/bin/ruby

str="Hello Ruby!"
putc str
```

以上实例运行输出结果为：

```text
H
```


## print 语句

print 语句与 puts 语句类似。唯一的不同在于 puts 语句在输出内容后会跳到下一行，而使用 print 语句时，光标定位在同一行。


## 实例

```java
#!/usr/bin/ruby

print "Hello World"
print "Good Morning"
```

以上实例运行输出结果为：

```text
Hello WorldGood Morning
```


## 打开和关闭文件

截至现在，您已经读取并写入标准输入和输出。现在，我们将看看如何操作实际的数据文件。


### File.new 方法

您可以使用 File.new 方法创建一个 File 对象用于读取、写入或者读写，读写权限取决于 mode 参数。最后，您可以使用 File.close 方法来关闭该文件。


## 语法

```text
aFile = File.new("filename", "mode")
   # ... 处理文件
aFile.close
```


### File.open 方法

您可以使用 File.open 方法创建一个新的 file 对象，并把该 file 对象赋值给文件。但是，File.open 和 File.new 方法之间有一点不同。不同点是 File.open 方法可与块关联，而 File.new 方法不能。

```text
File.open("filename", "mode") do |aFile|
   # ... process the file
end
```

下表列出了打开文件的不同模式：


## 读取和写入文件

用于简单 I/O 的方法也可用于所有 file 对象。所以，gets 从标准输入读取一行，aFile.gets 从文件对象 aFile 读取一行。

但是，I/O 对象提供了访问方法的附加设置，为我们提供了便利。


### sysread 方法

您可以使用方法 sysread 来读取文件的内容。当使用方法 sysread 时，您可以使用任意一种模式打开文件。例如：

下面是输入文本文件：

```text
This is a simple text file for testing purpose.
```

现在让我们尝试读取这个文件：


## 实例

```text
#!/usr/bin/ruby

aFile = File.new("input.txt", "r")
if aFile
   content = aFile.sysread(20)
   puts content
else
   puts "Unable to open file!"
end
```

该语句将输入文件的头 20 个字符。文件指针将被放置在文件中第 21 个字符的位置。


### syswrite 方法

您可以使用方法 syswrite 来向文件写入内容。当使用方法 syswrite 时，您需要以写入模式打开文件。例如：


## 实例

```text
#!/usr/bin/ruby

aFile = File.new("input.txt", "r+")
if aFile
   aFile.syswrite("ABCDEF")
else
   puts "Unable to open file!"
end
```

该语句将写入 "ABCDEF" 到文件中。


### each_byte 方法

该方法属于类 File。方法 each_byte 是个可以迭代字符串中每个字符。请看下面的代码实例：


## 实例

```text
#!/usr/bin/ruby

aFile = File.new("input.txt", "r+")
if aFile
   aFile.syswrite("ABCDEF")
   aFile.rewind
   aFile.each_byte {|ch| putc ch; putc ?. }
else
   puts "Unable to open file!"
end
```

字符一个接着一个被传到变量 ch，然后显示在屏幕上，如下所示：

```text
A.B.C.D.E.F.s. .a. .s.i.m.p.l.e. .t.e.x.t. .f.i.l.e. .f.o.r. .t.e.s.t.i.n.g. .p.u.r.p.o.s.e...
```


### IO.readlines 方法

类 File 是类 IO 的一个子类。类 IO 也有一些用于操作文件的方法。

IO.readlines 是 IO 类中的一个方法。该方法逐行返回文件的内容。下面的代码显示了方法 IO.readlines 的使用：


## 实例

```text
#!/usr/bin/ruby

arr = IO.readlines("input.txt")
puts arr[0]
puts arr[1]
```

在这段代码中，变量 arr 是一个数组。文件 input.txt 的每一行将是数组 arr 中的一个元素。因此，arr[0] 将包含第一行，而 arr[1] 将包含文件的第二行。


### IO.foreach 方法

该方法也逐行返回输出。方法 foreach 与方法 readlines 之间不同的是，方法 foreach 与块相关联。但是，不像方法 readlines，方法 foreach 不是返回一个数组。例如：


## 后续章节

- 实例
- 重命名和删除文件
- 实例
- 实例
- 文件模式与所有权
- 实例
- 文件查询
- 实例
- 实例
- 实例
- 实例
- 实例
- 实例
- 实例
- 实例
- Ruby 中的目录

## 复习重点

- 能说明 `Ruby 文件的输入与输出` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
