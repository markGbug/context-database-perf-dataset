# Go：Go 语言Map(集合)

- 来源：[Go 语言 Map(集合)](https://www.runoob.com/go/go-map.html)
- 分类：后端开发
- 技术：Go
- 笔记类型：练习笔记
- 章节序号：0863

## 本章内容

Map 是一种无序的键值对的集合。

Map 最重要的一点是通过 key 来快速检索数据，key 类似于索引，指向数据的值。

Map 是一种集合，所以我们可以像迭代数组和切片那样迭代它。不过，Map 是无序的，遍历 Map 时返回的键值对的顺序是不确定的。

在获取 Map 的值时，如果键不存在，返回该类型的零值，例如 int 类型的零值是 0，string 类型的零值是 ""。

Map 是引用类型，如果将一个 Map 传递给一个函数或赋值给另一个变量，它们都指向同一个底层数据结构，因此对 Map 的修改会影响到所有引用它的变量。


### 定义 Map

可以使用内建函数 make 或使用 map 关键字来定义 Map:

```text
/* 使用 make 函数 */
map_variable := make(map[KeyType]ValueType, initialCapacity)
```

其中 KeyType 是键的类型，ValueType 是值的类型，initialCapacity 是可选的参数，用于指定 Map 的初始容量。Map 的容量是指 Map 中可以保存的键值对的数量，当 Map 中的键值对数量达到容量时，Map 会自动扩容。如果不指定 initialCapacity，Go 语言会根据实际情况选择一个合适的值。


## 实例

也可以使用字面量创建 Map：

```text
// 使用字面量创建 Map
m := map[string]int{
    "apple": 1,
    "banana": 2,
    "orange": 3,
}
```

获取元素：

```text
// 获取键值对
v1 := m["apple"]
v2, ok := m["pear"]  // 如果键不存在，ok 的值为 false，v2 的值为该类型的零值
```

修改元素：

```text
// 修改键值对
m["apple"] = 5
```

获取 Map 的长度：

```text
// 获取 Map 的长度
len := len(m)
```

遍历 Map：

```text
// 遍历 Map
for k, v := range m {
    fmt.Printf("key=%s, value=%d\n", k, v)
}
```

删除元素：

```text
// 删除键值对
delete(m, "banana")
```


### 实例

下面实例演示了创建和使用map:


## 实例

以上实例运行结果为：

```text
Wiki 首都是 维基百科
Google 首都是 谷歌
Runoob 首都是 菜鸟教程
Baidu 首都是 百度
Facebook 站点不存在
```


## delete() 函数

delete() 函数用于删除集合的元素, 参数为 map 和其对应的 key。实例如下：


## 实例

以上实例运行结果为：

```text
原始地图
India 首都是 New delhi
France 首都是 Paris
Italy 首都是 Rome
Japan 首都是 Tokyo
法国条目被删除
删除元素后地图
Italy 首都是 Rome
Japan 首都是 Tokyo
India 首都是 New delhi
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Go 语言 Map(集合)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
