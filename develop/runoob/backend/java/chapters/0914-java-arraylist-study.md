# Java：Java ArrayList

- 来源：[Java ArrayList](https://www.runoob.com/java/java-arraylist.html)
- 分类：后端开发
- 技术：Java
- 笔记类型：学习笔记
- 章节序号：0914

## 本章内容

Java 集合框架

ArrayList 类是一个可以动态修改的数组，与普通数组的区别就是它是没有固定大小的限制，我们可以添加或删除元素。

ArrayList 继承了 AbstractList ，并实现了 List 接口。

ArrayList 类位于 java.util 包中，使用前需要引入它，语法格式如下：

```html
import java.util.ArrayList; // 引入 ArrayList 类

ArrayList<E> objectName =new ArrayList<>();　 // 初始化
```

- E: 泛型数据类型，用于设置 objectName 的数据类型，只能为引用数据类型。
- objectName: 对象名。

ArrayList 是一个数组队列，提供了相关的添加、删除、修改、遍历等功能。


### 添加元素

ArrayList 类提供了很多有用的方法，添加元素到 ArrayList 可以使用 add() 方法:


## 实例

以上实例，执行输出结果为：

```text
[Google, Runoob, Taobao, Weibo]
```


### 访问元素

访问 ArrayList 中的元素可以使用 get() 方法：


## 实例

注意：数组的索引值从 0 开始。

以上实例，执行输出结果为：

```text
Runoob
```


### 修改元素

如果要修改 ArrayList 中的元素可以使用 set() 方法， set(int index, E element) 方法的第一个参数是索引（index），表示要替换的元素的位置，第二个参数是新元素（element），表示要设置的新值：


## 实例

以上实例，执行输出结果为：

```text
[Google, Runoob, Wiki, Weibo]
```


### 删除元素

如果要删除 ArrayList 中的元素可以使用 remove() 方法：


## 实例

以上实例，执行输出结果为：

```text
[Google, Runoob, Taobao]
```


### 计算大小

如果要计算 ArrayList 中的元素数量可以使用 size() 方法：


## 实例

以上实例，执行输出结果为：

```text
4
```


### 迭代数组列表

我们可以使用 for 来迭代数组列表中的元素：


## 实例

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


### 其他的引用类型

ArrayList 中的元素实际上是对象，在以上实例中，数组列表元素都是字符串 String 类型。

如果我们要存储其他类型，而 <E> 只能为引用数据类型，这时我们就需要使用到基本类型的包装类。

基本类型对应的包装类表如下：

此外，BigInteger、BigDecimal 用于高精度的运算，BigInteger 支持任意精度的整数，也是引用类型，但它们没有相对应的基本类型。

```html
ArrayList<Integer> li=new ArrayList<>();     // 存放整数元素
ArrayList<Character> li=new ArrayList<>();   // 存放字符元素
```

以下实例使用 ArrayList 存储数字(使用 Integer 类型):


## 实例

以上实例，执行输出结果为：

```text
10
15
20
25
```


### ArrayList 排序

Collections 类也是一个非常有用的类，位于 java.util 包中，提供的 sort() 方法可以对字符或数字列表进行排序。

以下实例对字母进行排序：


## 实例

以上实例，执行输出结果为：

```text
Google
Runoob
Taobao
Weibo
Wiki
```

以下实例对数字进行排序：


## 实例

以上实例，执行输出结果为：

```text
8
12
15
20
33
34
```


## Java ArrayList 方法

Java ArrayList 常用方法列表如下：

更多 API 方法可以查看：https://www.runoob.com/manual/jdk11api/java.base/java/util/ArrayList.html

Java 集合框架


## 复习重点

- 能说明 `Java ArrayList` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
