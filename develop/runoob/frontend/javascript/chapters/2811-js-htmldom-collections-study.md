# JavaScript：JavaScript HTML DOM 集合(Collection)

- 来源：[HTMLCollection 对象](https://www.runoob.com/js/js-htmldom-collections.html)
- 分类：前端开发
- 技术：JavaScript
- 笔记类型：学习笔记
- 章节序号：2811

## 本章内容

本章节介绍 DOM 集合的使用。


## HTMLCollection 对象

getElementsByTagName() 方法返回 HTMLCollection 对象。

HTMLCollection 对象类似包含 HTML 元素的一个数组。

以下代码获取文档所有的 <p> 元素：


## 实例

```javascript
var x = document.getElementsByTagName("p");
```

集合中的元素可以通过索引(以 0 为起始位置)来访问。

访问第二个 <p> 元素可以是以下代码:


## HTMLCollection 对象 length 属性

HTMLCollection 对象的 length 属性定义了集合中元素的数量。


## 实例

```javascript
var myCollection = document.getElementsByTagName("p");
document.getElementById("demo").innerHTML = myCollection.length;
```


### 实例解析

获取 <p> 元素的集合：

```javascript
var myCollection = document.getElementsByTagName("p");
```

显示集合元素个数：

```text
document.getElementById("demo").innerHTML = myCollection.length;
```

集合 length 属性常用于遍历集合中的元素。


## 实例

修改所有 <p> 元素的背景颜色:

```java
var myCollection = document.getElementsByTagName("p");
var i;
for (i = 0; i < myCollection.length; i++) {
    myCollection[i].style.backgroundColor = "red";
}
```


### 注意

HTMLCollection 不是一个数组！

HTMLCollection 看起来可能是一个数组，但其实不是。

你可以像数组一样，使用索引来获取元素。

HTMLCollection 无法使用数组的方法： valueOf(), pop(), push(), 或 join() 。


## 复习重点

- 能说明 `HTMLCollection 对象` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
