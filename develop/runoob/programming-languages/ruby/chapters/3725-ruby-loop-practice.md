# Ruby：Ruby 循环

- 来源：[Ruby 循环](https://www.runoob.com/ruby/ruby-loop.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：练习笔记
- 章节序号：3725

## 本章内容

Ruby 中的循环用于执行相同的代码块若干次。本章节将详细介绍 Ruby 支持的所有循环语句。


## Ruby while 语句


## 语法

```java
while conditional [do]
   code
end
```

或者


## 语法

```java
while conditional [:]
   code
end
```

当 conditional 为真时，执行 code。

语法中 do 或 : 可以省略不写。但若要在一行内写出 while 式，则必须以 do 或 : 隔开条件式或程式区块。


## 实例

```java
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

$i = 0
$num = 5

while $i < $num  do
   puts("在循环语句中 i = #$i" )
   $i +=1
end
```

以上实例输出结果为：

```text
在循环语句中 i = 0
在循环语句中 i = 1
在循环语句中 i = 2
在循环语句中 i = 3
在循环语句中 i = 4
```


## Ruby while 修饰符


## 语法

```java
code while condition

或者

begin
  code
end while conditional
```

当 conditional 为真时，执行 code。

如果 while 修饰符跟在一个没有 rescue 或 ensure 子句的 begin 语句后面，code 会在 conditional 判断之前执行一次。


## 实例

```java
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

$i = 0
$num = 5
begin
   puts("在循环语句中 i = #$i" )
   $i +=1
end while $i < $num
```

以上实例输出结果为：

```text
在循环语句中 i = 0
在循环语句中 i = 1
在循环语句中 i = 2
在循环语句中 i = 3
在循环语句中 i = 4
```


## Ruby until 语句


## 语法

```text
until conditional [do]
   code
end
```

当 conditional 为假时，执行 code。

语法中 do 可以省略不写。但若要在一行内写出 until 式，则必须以 do 隔开条件式或程式区块。


## 实例

```text
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

$i = 0
$num = 5

until $i > $num  do
   puts("在循环语句中 i = #$i" )
   $i +=1;
end
```

以上实例输出结果为：

```text
在循环语句中 i = 0
在循环语句中 i = 1
在循环语句中 i = 2
在循环语句中 i = 3
在循环语句中 i = 4
在循环语句中 i = 5
```


## Ruby until 修饰符


## 语法

```text
code until conditional

或者

begin
   code
end until conditional
```

当 conditional 为 false 时，执行 code。

如果 until 修饰符跟在一个没有 rescue 或 ensure 子句的 begin 语句后面，code 会在 conditional 判断之前执行一次。


## 实例

```text
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

$i = 0
$num = 5
begin
   puts("在循环语句中 i = #$i" )
   $i +=1;
end until $i > $num
```

以上实例输出结果为：

```text
在循环语句中 i = 0
在循环语句中 i = 1
在循环语句中 i = 2
在循环语句中 i = 3
在循环语句中 i = 4
在循环语句中 i = 5
```


## Ruby for 语句


## 语法

```text
for variable [, variable ...] in expression [do]
   code
end
```

先计算表达式得到一个对象，然后针对 expression 中的每个元素分别执行一次 code。


## 实例

```text
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

for i in 0..5
   puts "局部变量的值为 #{i}"
end
```

在这里，我们已经定义了范围 0..5。语句 for i in 0..5 允许 i 的值从 0 到 5（包含 5）。

以上实例输出结果为：

```text
局部变量的值为 0
局部变量的值为 1
局部变量的值为 2
局部变量的值为 3
局部变量的值为 4
局部变量的值为 5
```

for...in 循环几乎是完全等价于：

```text
(expression).each do |variable[, variable...]| code end
```

但是，for 循环不会为局部变量创建一个新的作用域。

语法中 do 可以省略不写。但若要在一行内写出 for 式，则必须以 do 隔开条件式或程式区块。


## 实例

```text
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

(0..5).each do |i|
   puts "局部变量的值为 #{i}"
end
```

以上实例输出结果为：

```text
局部变量的值为 0
局部变量的值为 1
局部变量的值为 2
局部变量的值为 3
局部变量的值为 4
局部变量的值为 5
```


## Ruby break 语句


## 语法

```text
break
```

终止最内部的循环。如果在块内调用，则终止相关块的方法（方法返回 nil）。


## 实例

```text
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

for i in 0..5
   if i > 2 then
      break
   end
   puts "局部变量的值为 #{i}"
end
```

以上实例输出结果为：

```text
局部变量的值为 0
局部变量的值为 1
局部变量的值为 2
```


## Ruby next 语句


## 语法

```text
next
```

跳到循环的下一个迭代。如果在块内调用，则终止块的执行（yield 表达式返回 nil）。


## 实例

```text
#!/usr/bin/ruby
# -*- coding: UTF-8 -*-

for i in 0..5
   if i < 2 then
      next
   end
   puts "局部变量的值为 #{i}"
end
```

以上实例输出结果为：

```text
局部变量的值为 2
局部变量的值为 3
局部变量的值为 4
局部变量的值为 5
```


## Ruby redo 语句


## 后续章节

- 语法
- 实例
- Ruby retry 语句
- 语法
- 实例

## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ruby 循环` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
