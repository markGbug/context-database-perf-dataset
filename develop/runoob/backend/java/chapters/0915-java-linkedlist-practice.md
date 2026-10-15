# Java：Java LinkedList

- 来源：[Java LinkedList](https://www.runoob.com/java/java-linkedlist.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：练习笔记
- 章节序号：0915

## 本章内容

Java 集合框架

链表（Linked list）是一种常见的基础数据结构，是一种线性表，但是并不会按线性的顺序存储数据，而是在每一个节点里存到下一个节点的地址。

链表可分为单向链表和双向链表。

一个单向链表包含两个值: 当前节点的值和一个指向下一个节点的链接。

一个双向链表有三个整数值: 数值、向后的节点链接、向前的节点链接。

Java LinkedList（链表） 类似于 ArrayList，是一种常用的数据容器。

与 ArrayList 相比，LinkedList 的增加和删除的操作效率更高，而查找和修改的操作效率较低。

以下情况使用 ArrayList :

- 频繁访问列表中的某一个元素。
- 只需要在列表末尾进行添加和删除元素操作。

以下情况使用 LinkedList :

- 你需要通过循环迭代来访问列表中的某些元素。
- 需要频繁的在列表开头、中间、末尾等位置进行添加和删除元素操作。

LinkedList 继承了 AbstractSequentialList 类。

LinkedList 实现了 Queue 接口，可作为队列使用。

LinkedList 实现了 List 接口，可进行列表的相关操作。

LinkedList 实现了 Deque 接口，可作为队列使用。

LinkedList 实现了 Cloneable 接口，可实现克隆。


## 实例

以上实例，执行输出结果为：

```text
[Google, Runoob, Taobao, Weibo]
```

更多的情况下我们使用 ArrayList 访问列表中的随机元素更加高效，但以下几种情况 LinkedList 提供了更高效的方法。

在列表开头添加元素：


## 实例

以上实例，执行输出结果为：

```text
[Wiki, Google, Runoob, Taobao]
```

在列表结尾添加元素：


## 实例

以上实例，执行输出结果为：

```text
[Google, Runoob, Taobao, Wiki]
```

在列表开头移除元素：


## 实例

以上实例，执行输出结果为：

```text
[Runoob, Taobao, Weibo]
```

在列表结尾移除元素：


## 实例

以上实例，执行输出结果为：

```text
[Google, Runoob, Taobao]
```

获取列表开头的元素：


## 实例

以上实例，执行输出结果为：

```text
Google
```

获取列表结尾的元素：


## 实例

以上实例，执行输出结果为：

```text
Weibo
```


### 迭代元素

我们可以使用 for 配合 size() 方法来迭代列表中的元素：


## 实例

size() 方法用于计算链表的大小。

以上实例，执行输出结果为：

```text
Google
Runoob
Taobao
Weibo
```

也可以使用 for-each 来迭代元素：


## 实例

以上实例，执行输出结果为：

```text
Google
Runoob
Taobao
Weibo
```


### 常用方法

更多 API 方法可以查看：https://www.runoob.com/manual/jdk11api/java.base/java/util/LinkedList.html

Java 集合框架


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Java LinkedList` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
