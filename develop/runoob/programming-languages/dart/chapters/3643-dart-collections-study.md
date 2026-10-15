# Dart：Dart 集合类型

- 来源：[Dart 集合类型](https://www.runoob.com/dart/dart-collections.html)
- 分类：编程语言
- 技术：Dart
- 笔记类型：学习笔记
- 章节序号：3643

## 本章内容

集合是用来存放多个数据的数据结构。

Dart 内置了三种核心集合类型：List（列表）、Set（集合）和 Map（映射），本章将逐一介绍它们的用法。


## List：有序列表

List 是最常用的集合类型，用于存放一组有序的元素，允许重复。

你可以通过索引（从 0 开始）来访问 List 中的任意元素。


### 创建 List


## 实例

```text
网站列表: [RUNOOB, Google, GitHub]
数字列表: [1, 2, 3, 4, 5]
填充列表: [0, 0, 0]
平方数列表: [0, 1, 4, 9, 16]
```


### 访问和修改 List 元素


## 实例

```text
第一个水果: 苹果
最后一个: 橙子
修改后: [苹果, 葡萄, 橙子]
水果数量: 3
列表为空? false
列表非空? true
```


### List 常用操作


## 实例

```text
添加后: [RUNOOB, Dart, Flutter, Google, AI]
插入后: [RUNOOB, 教程, Dart, Flutter, Google, AI]
删除后: [教程, Dart, Flutter]
包含 Dart? true, 位置: 1
排序后: [1, 1, 3, 4, 5, 9]
反转后: [9, 5, 4, 3, 1, 1]
前3个: [1, 1, 3]
```


### List 的函数式方法

Dart 的 List 支持 map、where、reduce 等函数式方法，让数据处理更加简洁。


## 实例

```text
及格分数: (78, 92, 60, 88)
评级: (不及格, 及格, 及格, 及格, 不及格, 及格)
高分列表: [高分: 92, 高分: 88]
RUNOOB 总分: 418
平均分: 69.7
有满分吗? false
全部及格? false
```

map() 和 where() 返回的是 Iterable（惰性求值），需要用 toList() 转换为 List 才会真正执行计算。如果你只需要遍历一次，直接用 Iterable 即可，不需要转换。


## Set：唯一元素集合

Set 和 List 类似，但 Set 中的每个元素只能出现一次，不允许重复。

Set 是无序的，不能通过索引访问元素。


## 实例

```text
标签集合: {Dart, Flutter, RUNOOB}
标签数量: 3
添加后: {Dart, Flutter, RUNOOB, Google}
删除后: {Dart, Flutter, RUNOOB}
包含 RUNOOB? true
交集: {3, 4}
并集: {1, 2, 3, 4, 5, 6}
差集: {1, 2}
```

Set 的典型使用场景是"去重"——当你不需要重复元素时，用 Set 比用 List 手动去重要高效得多。


## Map：键值对映射

Map 用于存储键值对（Key-Value Pair），每个键对应一个值。

键在 Map 中必须是唯一的，值可以重复。


### 创建和访问 Map


## 实例

```text
站点名称: RUNOOB
站点 URL: https://www.runoob.com
描述: null
更新后: {name: RUNOOB.COM, url: https://www.runoob.com, type: 编程教程, language: 中文}
所有键: (name, url, type, language)
所有值: (RUNOOB.COM, https://www.runoob.com, 编程教程, 中文)
有 url 键? true
有 desc 键? false
```


### Map 常用操作


## 实例

```text
runoob: 95 分
Alice: 87 分
Bob: 72 分
删除 Bob 后: {runoob: 95, Alice: 87}
Alice: 87, Eve: 0
最终: {runoob: 95, Alice: 87, David: 80}
人数: 3
```

Map 的键可以是任何类型（String、int 等），但必须保证键的相等性有意义。使用自定义对象作为键时，需要确保正确实现了 == 和 hashCode。


## 集合展开运算符 ... 与 ...?

展开运算符可以将一个集合的元素"展开"到另一个集合中。


## 实例

```text
所有课程: [RUNOOB 入门, Dart, Flutter, 异步编程, 状态管理]
安全展开: [第一项]
有值展开: [第一项, 额外内容]
```


### 集合中的 if 和 for（集合控制流）

Dart 允许在集合字面量中直接使用 if 和 for，这是非常实用的语法糖。


## 实例

```text
菜单: [首页, 教程, 管理后台, 关于]
翻倍: [2, 4, 6]
链接: [RUNOOB 首页, https://runoob.com/Dart, https://runoob.com/Flutter]
```


## 三种集合对比


### 注意事项

Set 和 Map 都使用 {} 作为字面量。

区别在于：

- Map 使用 key: value 形式（有冒号）
- Set 直接写元素（没有冒号）

例如：

```javascript
var map = {'name': 'Tom'};   // Map
var set = {'Tom', 'Jerry'}; // Set
```

需要特别注意：

```javascript
var x = {};
```

这不会创建空 Set，而会被 Dart 推断为：

```html
Map<dynamic, dynamic>
```

因为空花括号无法判断元素类型，Dart 默认按 Map 处理。

如果要创建空 Set，必须显式指定：

```html
var x = <String>{};
```

或

```html
Set<String> x = {};
```


## 复习重点

- 能说明 `Dart 集合类型` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
