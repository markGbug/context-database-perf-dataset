# Ruby：Ruby 运算符

- 来源：[Ruby 运算符](https://www.runoob.com/ruby/ruby-operator.html)
- 分类：编程语言
- 技术：Ruby
- 笔记类型：练习笔记
- 章节序号：3722

## 本章内容

Ruby 支持一套丰富的运算符。大多数运算符实际上是方法调用。例如，a + b 被解释为 a.+(b)，其中指向变量 a 的 + 方法被调用，b 作为方法调用的参数。

对于每个运算符（+ - * / % ** & | ^ << >> && ||），都有一个相对应的缩写赋值运算符（+= -= 等等）。


## Ruby 算术运算符

假设变量 a 的值为 10，变量 b 的值为 20，那么：


## Ruby 比较运算符

假设变量 a 的值为 10，变量 b 的值为 20，那么：


## Ruby 赋值运算符

假设变量 a 的值为 10，变量 b 的值为 20，那么：


## Ruby 并行赋值

Ruby 也支持变量的并行赋值。这使得多个变量可以通过一行的 Ruby 代码进行初始化。例如：

```text
a = 10
b = 20
c = 30
```

使用并行赋值可以更快地声明：

```text
a, b, c = 10, 20, 30
```

并行赋值在交换两个变量的值时也很有用：

```text
a, b = b, c
```


## Ruby 位运算符

位运算符作用于位，并逐位执行操作。

假设如果 a = 60，且 b = 13，现在以二进制格式，它们如下所示：

a = 0011 1100

b = 0000 1101

-----------------

a&b = 0000 1100

a|b = 0011 1101

a^b = 0011 0001

~a = 1100 0011

下表列出了 Ruby 支持的位运算符。


## Ruby 逻辑运算符

下表列出了 Ruby 支持的逻辑运算符。

假设变量 a 的值为 10，变量 b 的值为 20，那么：


## Ruby 三元运算符

有一个以上的操作称为三元运算符。第一个计算表达式的真假值，然后根据这个结果决定执行后边两个语句中的一个。条件运算符的语法如下：


## Ruby 范围运算符

在 Ruby 中，序列范围用于创建一系列连续的值 - 包含起始值、结束值（视情况而定）和它们之间的值。

在 Ruby 中，这些序列是使用 ".." 和 "..." 范围运算符来创建的。两点形式创建的范围包含起始值和结束值，三点形式创建的范围只包含起始值不包含结束值。


## Ruby defined? 运算符

defined? 是一个特殊的运算符，以方法调用的形式来判断传递的表达式是否已定义。它返回表达式的描述字符串，如果表达式未定义则返回 nil。

下面是 defined? 运算符的各种用法：


## 用法 1

```text
defined? variable # 如果 variable 已经初始化，则为 True
```

例如：

```text
foo = 42
defined? foo    # => "local-variable"
defined? $_     # => "global-variable"
defined? bar    # => nil（未定义）
```


## 用法 2

```text
defined? method_call # 如果方法已经定义，则为 True
```

例如：

```text
defined? puts        # => "method"
defined? puts(bar)   # => nil（在这里 bar 未定义）
defined? unpack      # => nil（在这里未定义）
```


## 用法 3

```text
# 如果存在可被 super 用户调用的方法，则为 True
defined? super
```

例如：

```text
defined? super     # => "super"（如果可被调用）
defined? super     # => nil（如果不可被调用）
```


## 用法 4

```text
defined? yield   # 如果已传递代码块，则为 True
```

例如：

```text
defined? yield    # => "yield"（如果已传递块）
defined? yield    # => nil（如果未传递块）
```


## Ruby 点运算符 "." 和双冒号运算符 "::"

你可以通过在方法名称前加上类或模块名称和 . 来调用类或模块中的方法。你可以使用类或模块名称和两个冒号 :: 来引用类或模块中的常量。

:: 是一元运算符，允许在类或模块内定义常量、实例方法和类方法，可以从类或模块外的任何地方进行访问。

请记住：在 Ruby 中，类和方法也可以被当作常量。

你只需要在表达式的常量名前加上 :: 前缀，即可返回适当的类或模块对象。

如果 :: 前的表达式为类或模块名称，则返回该类或模块内对应的常量值；如果 :: 前未没有前缀表达式，则返回主Object类中对应的常量值。 。

下面是两个实例：

```text
MR_COUNT = 0        # 定义在主 Object 类上的常量
module Foo
  MR_COUNT = 0
  ::MR_COUNT = 1    # 设置全局计数为 1
  MR_COUNT = 2      # 设置局部计数为 2
end
puts MR_COUNT       # 这是全局常量
puts Foo::MR_COUNT  # 这是 "Foo" 的局部常量
```

第二个实例：

```text
CONST = ' out there'
class Inside_one
   CONST = proc {' in there'}
   def where_is_my_CONST
      ::CONST + ' inside one'
   end
end
class Inside_two
   CONST = ' inside two'
   def where_is_my_CONST
      CONST
   end
end
puts Inside_one.new.where_is_my_CONST
puts Inside_two.new.where_is_my_CONST
puts Object::CONST + Inside_two::CONST
puts Inside_two::CONST + CONST
puts Inside_one::CONST
puts Inside_one::CONST.call + Inside_two::CONST
```


## Ruby 运算符的优先级

下表按照运算符的优先级从高到低列出了所有的运算符。

注意：在方法列标识为 是 的运算符实际上是方法，因此可以被重载。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Ruby 运算符` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
