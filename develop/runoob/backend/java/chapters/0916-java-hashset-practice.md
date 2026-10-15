# Java：Java HashSet

- 来源：[Java HashSet](https://www.runoob.com/java/java-hashset.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：练习笔记
- 章节序号：0916

## 本章内容

Java 集合框架

HashSet 基于 HashMap 来实现的，是一个不允许有重复元素的集合。

HashSet 允许有 null 值。

HashSet 是无序的，即不会记录插入的顺序。

HashSet 不是线程安全的， 如果多个线程尝试同时修改 HashSet，则最终结果是不确定的。 您必须在多线程访问时显式同步对 HashSet 的并发访问。

HashSet 实现了 Set 接口。

HashSet 中的元素实际上是对象，一些常见的基本类型可以使用它的包装类。

基本类型对应的包装类表如下：

HashSet 类位于 java.util 包中，使用前需要引入它，语法格式如下：

```text
import java.util.HashSet; // 引入 HashSet 类
```

以下实例我们创建一个 HashSet 对象 sites，用于保存字符串元素：

```html
HashSet<String> sites = new HashSet<String>();
```


### 添加元素

HashSet 类提供了很多有用的方法，添加元素可以使用 add() 方法:


## 实例

执行以上代码，输出结果如下：

```text
[Google, Runoob, Zhihu, Taobao]
```


### 判断元素是否存在

我们可以使用 contains() 方法来判断元素是否存在于集合当中:


## 实例

执行以上代码，输出结果如下：

```text
true
```


### 删除元素

我们可以使用 remove() 方法来删除集合中的元素:


## 实例

执行以上代码，输出结果如下：

```text
[Google, Runoob, Zhihu]
```

删除集合中所有元素可以使用 clear 方法：


## 实例

执行以上代码，输出结果如下：

```text
[]
```


### 计算大小

如果要计算 HashSet 中的元素数量可以使用 size() 方法：


## 实例

执行以上代码，输出结果如下：

```text
4
```


### 迭代 HashSet

可以使用 for-each 来迭代 HashSet 中的元素。


## 实例

执行以上代码，输出结果如下：

```text
Google
Runoob
Zhihu
Taobao
```


## HashSet 常用方法

更多 API 方法可以查看：https://www.runoob.com/manual/jdk11api/java.base/java/util/HashSet.html

Java 集合框架


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Java HashSet` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
