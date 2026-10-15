# C++：C++ vector 容器

- 来源：[C++ vector 容器](https://www.runoob.com/cplusplus/cpp-vector.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：练习笔记
- 章节序号：3560

## 本章内容

在 C++ 中，vector 是最常用的 STL 容器之一。

vector 本质上是一个可自动扩容的动态数组，与传统数组相比，vector 不需要手动管理内存，可以根据元素数量自动扩容。

由于 vector 具有：

- 连续内存存储
- 随机访问速度快
- STL 生态完整
- 缓存友好（Cache Friendly）

因此，在现代 C++ 开发中，大部分顺序数据存储场景都会优先考虑 vector。


### vector 的核心特点

- 动态大小：vector 可以自动扩容和缩容。
- 连续内存：元素在内存中连续存储，访问效率非常高。
- 随机访问：支持通过下标快速访问元素，时间复杂度为 O(1)。
- 自动内存管理：不需要手动 malloc/free。
- 支持迭代器：可以方便地与 STL 算法配合使用。


### 为什么 vector 很快？

vector 的元素在内存中是连续排列的：

```text
[1][2][3][4][5]
```

这种布局对 CPU Cache 非常友好。

CPU 在读取第一个元素时，通常会提前把后面的数据一起加载到缓存中，因此遍历 vector 的速度通常非常快。

这也是为什么很多情况下：

```text
vector 比 list 更快
```

即使 list 在理论上的删除复杂度更低。


### 使用 vector

使用 vector 前，需要包含头文件：

```html
#include <vector>
```


### 创建 vector

创建一个空 vector：

```html
std::vector<int>vec;
```

指定初始大小：

```html
std::vector<int>vec(5);
```

以上代码会创建 5 个元素，默认值为 0。

指定初始值：

```html
std::vector<int>vec(5, 10);
```

创建结果：

```text
[10, 10, 10, 10, 10]
```

使用初始化列表：

```html
std::vector<int>vec = {1, 2, 3, 4};
```


### 添加元素

使用 push_back() 向尾部添加元素：

```text
vec.push_back(100);
```

vector 尾部追加元素的平均时间复杂度为：

```text
O(1)
```


### 访问元素

使用下标访问：

```java
int x = vec[0];
```

使用 at()：

```java
int y = vec.at(1);
```

区别：

- [] 不检查越界，速度更快。
- at() 会检查越界，更安全。


### 获取大小

```text
vec.size();
```

返回当前元素数量。


### size 和 capacity 的区别

这是 vector 最重要的概念之一。

```html
std::vector<int>vec;

vec.push_back(1);
vec.push_back(2);

std::cout << vec.size() << std::endl;
std::cout << vec.capacity() << std::endl;
```

输出可能为：

```text
2
4
```

- size：当前元素数量。
- capacity：当前已分配的内存容量。

capacity 通常大于等于 size。

这是因为 vector 会提前申请更多空间，以减少频繁扩容。


### vector 扩容机制

当 vector 空间不足时，会发生扩容：

- 申请更大的内存
- 复制旧元素
- 释放旧内存

这个过程代价较高。

例如：

```java
std::vector<int>vec;

for (int i = 0; i < 1000000; i++) {
    vec.push_back(i);
}
```

可能发生多次内存重新分配。


### reserve() 预分配空间

为了避免频繁扩容，可以提前分配内存：

```html
std::vector<int>vec;

vec.reserve(1000000);
```

这样可以减少：

- 内存重新分配
- 元素复制
- 性能损耗

这是工程开发中非常重要的优化技巧。


### 遍历 vector

```java
for (size_t i = 0; i < vec.size(); i++) {
    std::cout << vec[i] << " ";
}
```

```java
for (auto it = vec.begin(); it != vec.end(); ++it) {
    std::cout << *it << " ";
}
```

```java
for (int element : vec) {
    std::cout << element << " ";
}
```


### 删除元素

删除第三个元素：

```text
vec.erase(vec.begin() + 2);
```

注意：

vector 删除中间元素时，后面的元素会整体前移。

例如：

```text
1 2 3 4 5

删除 2 后：

1 3 4 5
```

其中：

```text
3 4 5
```

都需要移动位置。

因此：

```text
erase() 的时间复杂度为 O(n)
```


### vector 不适合的场景

- 频繁头部插入
- 频繁中间删除
- 超大对象频繁扩容

例如：

```text
vec.insert(vec.begin(), 100);
```

这是一个较慢的操作。


### 迭代器失效

vector 扩容后，原来的内存地址可能失效。

例如：

```html
std::vector<int>vec = {1, 2, 3};

auto it = vec.begin();

vec.push_back(4);

std::cout << *it;
```

这里的 it 可能已经失效。

因为 push_back() 可能导致重新分配内存。

这是 vector 最常见的坑之一。


### clear() 的注意事项

```text
vec.clear();
```

clear() 只会清空元素：

- size 变为 0
- capacity 可能仍然保留

也就是说：

```text
clear() 不一定释放内存
```

如果希望释放内存：

```html
std::vector<int>().swap(vec);
```

或者：

```text
vec.shrink_to_fit();
```


### push_back 和 emplace_back

现代 C++ 更推荐使用：

```text
emplace_back()
```

例如：

```text
vec.push_back(Person("Tom", 20));
```

可能产生临时对象。

而：

```text
vec.emplace_back("Tom", 20);
```

会直接在 vector 内部原地构造对象。

通常效率更高。


### vector 与数组的区别


### vector 常见操作复杂度


## 实例：学生成绩管理


## 实例

输出结果如下：

```text
所有成绩: 85 90 78 92 88
平均成绩: 86.6
删除后成绩: 85 90 92 88
```


## 总结

vector 是现代 C++ 中最重要、最常用的数据结构之一。

它的核心优势：

- 动态扩容
- 连续内存
- 随机访问快
- 缓存友好
- STL 生态完整

但同时也需要注意：

- 扩容的性能代价
- 中间删除效率低
- 迭代器失效问题

对于绝大多数顺序存储场景：

```text
vector 通常都是默认首选容器
```


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `C++ vector 容器` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
