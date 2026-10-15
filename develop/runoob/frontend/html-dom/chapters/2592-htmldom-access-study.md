# HTML DOM：HTML DOM 访问

- 来源：[HTML DOM 访问](https://www.runoob.com/htmldom/htmldom-access.html)
- 分类：前端开发
- 技术：HTML DOM
- 笔记类型：学习笔记
- 章节序号：2592

## 本章内容

访问 HTML DOM - 查找 HTML 元素。


## 访问 HTML 元素（节点）

访问 HTML 元素等同于访问节点

您能够以不同的方式来访问 HTML 元素：

- 通过使用 getElementById() 方法
- 通过使用 getElementsByTagName() 方法
- 通过使用 getElementsByClassName() 方法


## getElementById() 方法

getElementById() 方法返回带有指定 ID 的元素引用：


### 语法

下面的例子获取 id="intro" 的元素：


## 实例

```text
document.getElementById("intro");
```


## getElementsByTagName() 方法

getElementsByTagName() 返回带有指定标签名的所有元素。


### 语法

下面的例子返回包含文档中所有 <p> 元素的列表：


## 实例 1

```text
document.getElementsByTagName("p");
```

下面的例子返回包含文档中所有 <p> 元素的列表，并且这些 <p> 元素应该是 id="main" 的元素的后代（子、孙等等）：


## 实例 2

```text
document.getElementById("main").getElementsByTagName("p");
```


## The getElementsByClassName() Method

如果您希望查找带有相同类名的所有 HTML 元素，请使用这个方法：

上面的例子返回包含 class="intro" 的所有元素的一个列表：

注意：getElementsByClassName() 在 Internet Explorer 5,6,7,8 中无效。


## 复习重点

- 能说明 `HTML DOM 访问` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
