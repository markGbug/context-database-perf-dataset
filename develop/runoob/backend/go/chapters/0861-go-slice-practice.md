# Go：Go 语言切片(Slice)

- 来源：[Go 语言切片(Slice)](https://www.runoob.com/go/go-slice.html)
- 分类：后端开发
- 技术：Go
- 笔记类型：练习笔记
- 章节序号：0861

## 本章内容

Go 语言切片是对数组的抽象。

Go 数组的长度不可改变，在特定场景中这样的集合就不太适用，Go 中提供了一种灵活，功能强悍的内置类型切片("动态数组")，与数组相比切片的长度是不固定的，可以追加元素，在追加时可能使切片的容量增大。


## 定义切片

你可以声明一个未指定大小的数组来定义切片：

```javascript
var identifier []type
```

切片不需要说明长度。

或使用 make() 函数来创建切片:

```javascript
var slice1 []type = make([]type, len)

也可以简写为

slice1 := make([]type, len)
```

也可以指定容量，其中 capacity 为可选参数。

```text
make([]T, length, capacity)
```

这里 len 是数组的长度并且也是切片的初始长度。


### 切片初始化

```java
s :=[] int {1,2,3 }
```

直接初始化切片，[] 表示是切片类型，{1,2,3} 初始化值依次是 1,2,3，其 cap=len=3。

```text
s := arr[:]
```

初始化切片 s，是数组 arr 的引用。

```text
s := arr[startIndex:endIndex]
```

将 arr 中从下标 startIndex 到 endIndex-1 下的元素创建为一个新的切片。

```text
s := arr[startIndex:]
```

默认 endIndex 时将表示一直到arr的最后一个元素。

```text
s := arr[:endIndex]
```

默认 startIndex 时将表示从 arr 的第一个元素开始。

```text
s1 := s[startIndex:endIndex]
```

通过切片 s 初始化切片 s1。

```text
s :=make([]int,len,cap)
```

通过内置函数 make() 初始化切片s，[]int 标识为其元素类型为 int 的切片。


## len() 和 cap() 函数

切片是可索引的，并且可以由 len() 方法获取长度。

切片提供了计算容量的方法 cap() 可以测量切片最长可以达到多少。

以下为具体实例：


## 实例

以上实例运行输出结果为:

```text
len=3 cap=5 slice=[0 0 0]
```


## 空(nil)切片

一个切片在未初始化之前默认为 nil，长度为 0，实例如下：


## 实例

以上实例运行输出结果为:

```text
len=0 cap=0 slice=[]
切片是空的
```


## 切片截取

可以通过设置下限及上限来设置截取切片 [lower-bound:upper-bound]，实例如下：


## 实例

执行以上代码输出结果为：

```text
len=9 cap=9 slice=[0 1 2 3 4 5 6 7 8]
numbers == [0 1 2 3 4 5 6 7 8]
numbers[1:4] == [1 2 3]
numbers[:3] == [0 1 2]
numbers[4:] == [4 5 6 7 8]
len=0 cap=5 slice=[]
len=2 cap=9 slice=[0 1]
len=3 cap=7 slice=[2 3 4]
```


## append() 和 copy() 函数

如果想增加切片的容量，我们必须创建一个新的更大的切片并把原分片的内容都拷贝过来。

下面的代码描述了从拷贝切片的 copy 方法和向切片追加新元素的 append 方法。


## 实例

以上代码执行输出结果为：

```text
len=0 cap=0 slice=[]
len=1 cap=1 slice=[0]
len=2 cap=2 slice=[0 1]
len=5 cap=6 slice=[0 1 2 3 4]
len=5 cap=12 slice=[0 1 2 3 4]
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Go 语言切片(Slice)` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
