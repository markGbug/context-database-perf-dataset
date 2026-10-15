# jQuery：jQuery - 删除元素

- 来源：[jQuery 删除元素](https://www.runoob.com/jquery/jquery-dom-remove.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：学习笔记
- 章节序号：2978

## 本章内容

通过 jQuery，可以很容易地删除已有的 HTML 元素。


## 删除元素/内容

如需删除元素和内容，一般可使用以下两个 jQuery 方法：

- remove() - 删除被选元素（及其子元素）
- empty() - 从被选元素中删除子元素


## jQuery remove() 方法

jQuery remove() 方法删除被选元素及其子元素。


## 实例

```text
$("#div1").remove();
```


## jQuery empty() 方法

jQuery empty() 方法删除被选元素的子元素。


## 实例

```text
$("#div1").empty();
```


## 过滤被删除的元素

jQuery remove() 方法也可接受一个参数，允许您对被删元素进行过滤。

该参数可以是任何 jQuery 选择器的语法。

下面的例子删除 class="italic" 的所有 <p> 元素：


## 实例

```text
$("p").remove(".italic");
```


## 复习重点

- 能说明 `jQuery 删除元素` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
