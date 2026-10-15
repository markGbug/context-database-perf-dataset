# jQuery：jQuery css() 方法

- 来源：[jQuery css() 方法](https://www.runoob.com/jquery/jquery-css.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：学习笔记
- 章节序号：2980

## 本章内容

## jQuery css() 方法

css() 方法设置或返回被选元素的一个或多个样式属性。


## 返回 CSS 属性

如需返回指定的 CSS 属性的值，请使用如下语法：

下面的例子将返回首个匹配元素的 background-color 值：


## 实例

```text
$("p").css("background-color");
```


## 设置 CSS 属性

如需设置指定的 CSS 属性，请使用如下语法：

下面的例子将为所有匹配元素设置 background-color 值：


## 实例

```text
$("p").css("background-color","yellow");
```


## 设置多个 CSS 属性

如需设置多个 CSS 属性，请使用如下语法：

下面的例子将为所有匹配元素设置 background-color 和 font-size：


## 实例

```text
$("p").css({"background-color":"yellow","font-size":"200%"});
```


## 复习重点

- 能说明 `jQuery css() 方法` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
