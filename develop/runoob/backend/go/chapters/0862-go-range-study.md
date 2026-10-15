# Go：Go 语言范围(Range)

- 来源：[Go 语言范围(Range)](https://www.runoob.com/go/go-range.html)
- 分类：后端开发
- 技术：Go
- 笔记类型：学习笔记
- 章节序号：0862

## 本章内容

Go 语言中 range 关键字用于 for 循环中迭代数组(array)、切片(slice)、通道(channel)或集合(map)的元素。在数组和切片中它返回元素的索引和索引对应的值，在集合中返回 key-value 对。

for 循环的 range 格式可以对 slice、map、数组、字符串等进行迭代循环。格式如下：

```text
for key, value := range oldMap {
    newMap[key] = value
}
```

以上代码中的 key 和 value 是可以省略。

如果只想读取 key，格式如下：

```text
for key := range oldMap
```

或者这样：

for key, _ := range oldMap

如果只想读取 value，格式如下：

```text
for _, value := range oldMap
```


## 实例


### 数组和切片

遍历简单的切片，2**%d 的结果为 2 对应的次方数：


## 实例

以上实例运行输出结果为：

```text
2**0 = 1
2**1 = 2
2**2 = 4
2**3 = 8
2**4 = 16
2**5 = 32
2**6 = 64
2**7 = 128
```


### 字符串

range 迭代字符串时，返回每个字符的索引和 Unicode 代码点（rune）。


## 实例

以上实例运行输出结果为:

```text
index: 0, char: h
index: 1, char: e
index: 2, char: l
index: 3, char: l
index: 4, char: o
```


### 映射（Map）

for 循环的 range 格式可以省略 key 和 value，如下实例：


## 实例

以上实例运行输出结果为:

```text
key is: 4 - value is: 4.000000
key is: 1 - value is: 1.000000
key is: 2 - value is: 2.000000
key is: 3 - value is: 3.000000
key is: 1
key is: 2
key is: 3
key is: 4
value is: 1.000000
value is: 2.000000
value is: 3.000000
value is: 4.000000
```


### 通道（Channel）

range 遍历从通道接收的值，直到通道关闭。


## 实例

以上实例运行输出结果为:

```text
1
2
```


### 忽略值

在遍历时可以使用 _ 来忽略索引或值。


## 实例

以上实例运行输出结果为:

```text
value: 2
value: 3
value: 4
index: 0
index: 1
index: 2
```


### 其他

range 遍历其他数据结构：


## 实例

以上实例运行输出结果为：

```text
sum: 9
index: 1
a -> apple
b -> banana
0 103
1 111
```


## 复习重点

- 能说明 `Go 语言范围(Range)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
