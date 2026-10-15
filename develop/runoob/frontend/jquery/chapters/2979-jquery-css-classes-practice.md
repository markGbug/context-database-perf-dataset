# jQuery：jQuery - 获取并设置 CSS 类

- 来源：[jQuery CSS 类](https://www.runoob.com/jquery/jquery-css-classes.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：练习笔记
- 章节序号：2979

## 本章内容

通过 jQuery，可以很容易地对 CSS 元素进行操作。 切换 CSS 类


## jQuery 操作 CSS

jQuery 拥有若干进行 CSS 操作的方法。我们将学习下面这些：

- addClass() - 向被选元素添加一个或多个类
- removeClass() - 从被选元素删除一个或多个类
- toggleClass() - 对被选元素进行添加/删除类的切换操作
- css() - 设置或返回样式属性


## 实例样式表

下面的样式表将用于本页的所有例子：

```text
.important {
    font-weight:bold;
    font-size:xx-large;
}

.blue {
    color:blue;
}
```


## jQuery addClass() 方法

下面的例子展示如何向不同的元素添加 class 属性。当然，在添加类时，您也可以选取多个元素：


## 实例

```text
$("button").click(function(){
  $("h1,h2,p").addClass("blue");
  $("div").addClass("important");
});
```

您也可以在 addClass() 方法中规定多个类：


## 实例

```text
$("button").click(function(){
  $("body div:first").addClass("important blue");
});
```


## jQuery removeClass() 方法

下面的例子演示如何在不同的元素中删除指定的 class 属性：


## 实例

```text
$("button").click(function(){
  $("h1,h2,p").removeClass("blue");
});
```


## jQuery toggleClass() 方法

下面的例子将展示如何使用 jQuery toggleClass() 方法。该方法对被选元素进行添加/删除类的切换操作：


## 实例

```text
$("button").click(function(){
  $("h1,h2,p").toggleClass("blue");
});
```


## jQuery css() 方法

我们将在下一章讲解 jQuery css() 方法。


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jQuery CSS 类` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
