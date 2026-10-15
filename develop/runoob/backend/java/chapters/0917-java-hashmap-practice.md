# Java：Java HashMap

- 来源：[Java HashMap](https://www.runoob.com/java/java-hashmap.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：练习笔记
- 章节序号：0917

## 本章内容

Java 集合框架

HashMap 是一个散列表，它存储的内容是键值对(key-value)映射。

HashMap 实现了 Map 接口，根据键的 HashCode 值存储数据，具有很快的访问速度，最多允许一条记录的键为 null，不支持线程同步。

HashMap 是无序的，即不会记录插入的顺序。

HashMap 继承于AbstractMap，实现了 Map、Cloneable、java.io.Serializable 接口。

HashMap 的 key 与 value 类型可以相同也可以不同，可以是字符串（String）类型的 key 和 value，也可以是整型（Integer）的 key 和字符串（String）类型的 value。

HashMap 中的元素实际上是对象，一些常见的基本类型可以使用它的包装类。

基本类型对应的包装类表如下：

HashMap 类位于 java.util 包中，使用前需要引入它，语法格式如下：

```text
import java.util.HashMap; // 引入 HashMap 类
```

以下实例我们创建一个 HashMap 对象 Sites， 整型（Integer）的 key 和字符串（String）类型的 value：

```html
HashMap<Integer, String> Sites = new HashMap<Integer, String>();
```


### 添加元素

HashMap 类提供了很多有用的方法，添加键值对(key-value)可以使用 put() 方法:


## 实例

执行以上代码，输出结果如下：

```text
{1=Google, 2=Runoob, 3=Taobao, 4=Zhihu}
```

以下实例创建一个字符串（String）类型的 key 和字符串（String）类型的 value：


## 实例

执行以上代码，输出结果如下：

```text
{four=Zhihu, one=Google, two=Runoob, three=Taobao}
```


### 访问元素

我们可以使用 get(key) 方法来获取 key 对应的 value:


## 实例

执行以上代码，输出结果如下：

```text
Taobao
```


### 删除元素

我们可以使用 remove(key) 方法来删除 key 对应的键值对(key-value):


## 实例

执行以上代码，输出结果如下：

```text
{1=Google, 2=Runoob, 3=Taobao}
```

删除所有键值对(key-value)可以使用 clear 方法：


## 实例

执行以上代码，输出结果如下：

```text
{}
```


### 计算大小

如果要计算 HashMap 中的元素数量可以使用 size() 方法：


## 实例

执行以上代码，输出结果如下：

```text
4
```


### 迭代 HashMap

可以使用 for-each 来迭代 HashMap 中的元素。

如果你只想获取 key，可以使用 keySet() 方法，然后可以通过 get(key) 获取对应的 value，如果你只想获取 value，可以使用 values() 方法。


## 实例

执行以上代码，输出结果如下：

```text
key: 1 value: Google
key: 2 value: Runoob
key: 3 value: Taobao
key: 4 value: Zhihu
Google, Runoob, Taobao, Zhihu,
```


## Java HashMap 方法

Java HashMap 常用方法列表如下：

更多 API 方法可以查看：https://www.runoob.com/manual/jdk11api/java.base/java/util/HashMap.html

Java 集合框架


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Java HashMap` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
