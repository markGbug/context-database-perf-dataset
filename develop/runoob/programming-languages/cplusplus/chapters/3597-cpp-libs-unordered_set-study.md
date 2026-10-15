# C++：C++ 容器类 <unordered_set>

- 来源：[C++ <unordered_set>](https://www.runoob.com/cplusplus/cpp-libs-unordered_set.html)
- 分类：编程语言
- 技术：C++
- 笔记类型：学习笔记
- 章节序号：3597

## 本章内容

在C++中，<unordered_set> 是标准模板库（STL）的一部分，提供了一种基于哈希表的容器，用于存储唯一的元素集合。

与 set 不同，unordered_set 不保证元素的排序，但通常提供更快的查找、插入和删除操作。

unordered_set 是一个模板类，其定义如下：

```html
#include <unordered_set>

std::unordered_set<Key, Hash = std::hash<Key>, Pred = std::equal_to<Key>, Alloc = std::allocator<Key>>
```

- Key 是存储在 unordered_set 中的元素类型。
- Hash 是一个函数或函数对象，用于生成元素的哈希值，默认为 std::hash<Key>。
- Pred 是一个二元谓词，用于比较两个元素是否相等，默认为 std::equal_to<Key>。
- Alloc 是分配器类型，用于管理内存分配，默认为 std::allocator<Key>。


### 语法

以下是一些基本的 unordered_set 操作：

- 构造函数：创建一个空的 unordered_set。 std::unordered_set<int> uset;
- 插入元素：使用 insert() 方法。 uset.insert(10);
- 查找元素：使用 find() 方法。 auto it = uset.find(10); if (it != uset.end()) { // 元素存在 }
- 删除元素：使用 erase() 方法。 uset.erase(10);
- 大小和空检查：使用 size() 和 empty() 方法。 size_t size = uset.size(); bool isEmpty = uset.empty();
- 清空容器：使用 clear() 方法。 uset.clear();


## 实例

下面是一个使用 unordered_set 的简单示例，包括输出结果。


## 实例

输出结果:

```text
Elements in uset: 10 20 30
Element 20 found in uset.
After erasing 20, elements in uset: 10 30
Size of uset: 2
Is uset empty? No
After clearing, is uset empty? Yes
```

unordered_set 是一个非常有用的容器，特别适合于需要快速查找、插入和删除操作的场景，同时不需要元素的有序性。


## 复习重点

- 能说明 `C++ <unordered_set>` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
