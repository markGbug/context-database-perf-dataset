# Lua：Lua 元表(Metatable)

- 来源：[Lua 元表(Metatable)](https://www.runoob.com/lua/lua-metatables.html)
- 分类：编程语言
- 技术：Lua
- 笔记类型：练习笔记
- 章节序号：3672

## 本章内容

在 Lua table 中我们可以访问对应的 key 来得到 value 值，但是却无法对两个 table 进行操作(比如相加)。

因此 Lua 提供了元表(Metatable)，允许我们改变 table 的行为，每个行为关联了对应的元方法。

例如，使用元表我们可以定义 Lua 如何计算两个 table 的相加操作 a+b。

当 Lua 试图对两个表进行相加时，先检查两者之一是否有元表，之后检查是否有一个叫 __add 的字段，若找到，则调用对应的值。 __add 等即时字段，其对应的值（往往是一个函数或是 table）就是"元方法"。

有两个很重要的函数来处理元表：

- setmetatable(table,metatable): 对指定 table 设置元表(metatable)，如果元表(metatable)中存在 __metatable 键值，setmetatable 会失败。
- getmetatable(table): 返回对象的元表(metatable)。

以下实例演示了如何对指定的表设置元表：

以上代码也可以直接写成一行：

```text
mytable = setmetatable({},{})
```

以下为返回对象元表：

```text
getmetatable(mytable)                 -- 这会返回 mymetatable
```


## __index 元方法

这是 metatable 最常用的键。

当你通过键来访问 table 的时候，如果这个键没有值，那么Lua就会寻找该table的metatable（假定有metatable）中的__index 键。如果__index包含一个表格，Lua会在表格中查找相应的键。

我们可以在使用 lua 命令进入交互模式查看：

如果__index包含一个函数的话，Lua就会调用那个函数，table和键会作为参数传递给函数。

__index 元方法查看表中元素是否存在，如果不存在，返回结果为 nil；如果存在则由 __index 返回结果。


## 实例

实例输出结果为：

```text
value1    metatablevalue
```

实例解析：

- mytable 表赋值为 {key1 = "value1"}。
- mytable 设置了元表，元方法为 __index。
- 在mytable表中查找 key1，如果找到，返回该元素，找不到则继续。
- 在mytable表中查找 key2，如果找到，返回 metatablevalue，找不到则继续。
- 判断元表有没有__index方法，如果__index方法是一个函数，则调用该函数。
- 元方法中查看是否传入 "key2" 键的参数（mytable.key2已设置），如果传入 "key2" 参数返回 "metatablevalue"，否则返回 mytable 对应的键值。

我们可以将以上代码简单写成：


### 总结

Lua 查找一个表元素时的规则，其实就是如下 3 个步骤:

- 1.在表中查找，如果找到，返回该元素，找不到则继续
- 2.判断该表是否有元表，如果没有元表，返回 nil，有元表则继续。
- 3.判断元表有没有 __index 方法，如果 __index 方法为 nil，则返回 nil；如果 __index 方法是一个表，则重复 1、2、3；如果 __index 方法是一个函数，则返回该函数的返回值。

该部分内容来自作者寰子：https://blog.csdn.net/xocoder/article/details/9028347


## __newindex 元方法

__newindex 元方法用来对表更新，__index则用来对表访问 。

当你给表的一个缺少的索引赋值，解释器就会查找__newindex 元方法：如果存在则调用这个函数而不进行赋值操作。

以下实例演示了 __newindex 元方法的应用：


## 实例

以上实例执行输出结果为：

```text
value1
nil    新值2
新值1    nil
```

以上实例中表设置了元方法 __newindex，在对新索引键（newkey）赋值时（mytable.newkey = "新值2"），会调用元方法，而不进行赋值。而如果对已存在的索引键（key1），则会进行赋值，而不调用元方法 __newindex。

以下实例使用了 rawset 函数来更新表：


## 实例

以上实例执行输出结果为：

```text
new value    "4"
```


## 为表添加操作符

以下实例演示了两表相加操作：


## 实例

以上实例执行输出结果为：

```text
1    1
2    2
3    3
4    4
5    5
6    6
```

__add 键包含在元表中，并进行相加操作。 表中对应的操作列表如下：(注意：__是两个下划线)


## __call 元方法

__call 元方法在 Lua 调用一个值时调用。以下实例演示了计算表中元素的和：


## 实例

以上实例执行输出结果为：

```text
70
```


## __tostring 元方法

__tostring 元方法用于修改表的输出行为。以下实例我们自定义了表的输出内容：


## 实例

以上实例执行输出结果为：

```text
表所有元素的和为 60
```

从本文中我们可以知道元表可以很好的简化我们的代码功能，所以了解 Lua 的元表，可以让我们写出更加简单优秀的 Lua 代码。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Lua 元表(Metatable)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
