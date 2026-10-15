# C++：C++ 容器类 <map>

- 来源：[C++ <map>](https://www.runoob.com/cplusplus/cpp-libs-map.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3598

## 本章内容

在 C++ 中，<map> 是标准模板库（STL）的一部分，它提供了一种关联容器，用于存储键值对（key-value pairs）。

map 容器中的元素是按照键的顺序自动排序的，这使得它非常适合需要快速查找和有序数据的场景。


### 定义和特性

- 键值对：map 存储的是键值对，其中每个键都是唯一的。
- 排序：map 中的元素按照键的顺序自动排序，通常是升序。
- 唯一性：每个键在 map 中只能出现一次。
- 双向迭代器：map 提供了双向迭代器，可以向前和向后遍历元素。


### 基本语法

包含头文件:

```html
#include <map>
```

声明 map 容器:

```html
std::map<key_type, value_type> myMap;
```

- key_type 是键的类型。
- value_type 是值的类型。

插入元素:

```text
myMap[key] = value;
```

访问元素:

```text
value = myMap[key];
```

遍历 map:

```java
for (std::map<key_type, value_type>::iterator it = myMap.begin(); it != myMap.end(); ++it) {
    std::cout << it->first << " => " << it->second << std::endl;
}
```

C++11 及以上标准，遍历部分可以简化为范围 for 循环，代码更简洁：

```java
for (auto &p : m) {
    std::cout << p.first << " : " << p.second << std::endl;
}
```


## 实例

下面是一个使用 map 的简单实例，我们将创建一个 map 来存储员工的姓名和他们的年龄，并遍历这个 map 来打印每个员工的姓名和年龄。


## 实例

输出结果:

```text
Alice is 30 years old.
Bob is 25 years old.
Charlie is 35 years old.
```


### 进阶用法

检查键是否存在:

```text
if (myMap.find(key) != myMap.end()) {
    // 键存在
}
```

删除元素:

```text
myMap.erase(key);
```

清空 map:

```text
myMap.clear();
```

获取 map 的大小:

```text
size_t size = myMap.size();
```

其他方法：

```text
myMap.empty();      // 是否为空
myMap.count("Bob"); // key 是否存在（返回 0 或 1）
```

自定义排序，默认升序排序，可以用 std::greater 或自定义比较函数：

```html
std::map<int, std::string, std::greater<int>> m;  // 降序
```

使用自定义比较函数:


## 实例

map 是 C++ STL 中一个非常有用的容器，特别适合需要快速查找和有序数据的场景。


## 实例

运行结果（自动按 key 排序）：

```text
Alice => 90
Bob => 85
Charlie => 92
Bob's score: 85
Size: 2
```


## 复习重点

- 能说明 `C++ <map>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
