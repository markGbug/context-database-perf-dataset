# Lua：Lua table(表)

- 来源：[Lua table(表)](https://www.runoob.com/lua/lua-tables.html)
- 分类：编程语言
- 技术：Lua
- 笔记类型：学习笔记
- 章节序号：3670

## 本章内容

table 是 Lua 的一种数据结构用来帮助我们创建不同的数据类型，如：数组、字典等。

Lua table 使用关联型数组，你可以用任意类型的值来作数组的索引，但这个值不能是 nil。

Lua table 是不固定大小的，你可以根据自己需要进行扩容。

Lua也是通过table来解决模块（module）、包（package）和对象（Object）的。 例如string.format表示使用"format"来索引table string。


## table(表)的构造

构造器是创建和初始化表的表达式。表是Lua特有的功能强大的东西。最简单的构造函数是{}，用来创建一个空表。可以直接初始化数组:

当我们为 table a 并设置元素，然后将 a 赋值给 b，则 a 与 b 都指向同一个内存。如果 a 设置为 nil ，则 b 同样能访问 table 的元素。如果没有指定的变量指向a，Lua的垃圾回收机制会清理相对应的内存。

以下实例演示了以上的描述情况：


## 实例

以上代码执行结果为：

```text
mytable 的类型是        table
mytable 索引为 1 的元素是       Lua
mytable 索引为 wow 的元素是     修改前
alternatetable 索引为 1 的元素是        Lua
alternatetable 索引为 wow 的元素是      修改前
mytable 索引为 wow 的元素是     修改后
alternatetable 是       nil
mytable 索引为 wow 的元素是     修改后
mytable 是      nil
```


## Table 操作

以下列出了 Table 操作常用的方法：

concat是concatenate(连锁, 连接)的缩写. table.concat()函数列出参数中指定table的数组部分从start位置到end位置的所有元素, 元素间以指定的分隔符(sep)隔开。

在table的数组部分指定位置(pos)插入值为value的一个元素. pos参数可选, 默认为数组部分末尾.

指定table中所有正数key值中最大的key值. 如果不存在key值为正数的元素, 则返回0。(Lua5.2之后该方法已经不存在了,本文使用了自定义函数实现)

返回table数组部分位于pos位置的元素. 其后的元素会被前移. pos参数可选, 默认为table长度, 即从最后一个元素删起。

对给定的table进行升序排序。


## 复习重点

- 能说明 `Lua table(表)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
