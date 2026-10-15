# jQuery：jQuery 效果 - 滑动

- 来源：[jQuery 滑动](https://www.runoob.com/jquery/jquery-slide.html)
- 分类：前端开发
- 技术：jQuery
- 笔记类型：学习笔记
- 章节序号：2970

## 本章内容

jQuery 滑动方法可使元素上下滑动。

点击这里，隐藏/显示面板

一寸光阴一寸金，因此，我们为您提供快捷易懂的学习内容。

在这里，您可以通过一种易懂的便利的模式获得您需要的任何知识。


## 实例

jQuery slideDown() 演示 jQuery slideDown() 方法。

jQuery slideUp() 演示 jQuery slideUp() 方法。

jQuery slideToggle() 演示 jQuery slideToggle() 方法。


## jQuery 滑动方法

通过 jQuery，您可以在元素上创建滑动效果。

jQuery 拥有以下滑动方法：

- slideDown()
- slideUp()
- slideToggle()


## jQuery slideDown() 方法

jQuery slideDown() 方法用于向下滑动元素。

语法:

可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是滑动完成后所执行的函数名称。

下面的例子演示了 slideDown() 方法：


## 实例

```text
$("#flip").click(function(){
  $("#panel").slideDown();
});
```


## jQuery slideUp() 方法

jQuery slideUp() 方法用于向上滑动元素。

语法:

可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是滑动完成后所执行的函数名称。

下面的例子演示了 slideUp() 方法：


## 实例

```text
$("#flip").click(function(){
  $("#panel").slideUp();
});
```


## jQuery slideToggle() 方法

jQuery slideToggle() 方法可以在 slideDown() 与 slideUp() 方法之间进行切换。

如果元素向下滑动，则 slideToggle() 可向上滑动它们。

如果元素向上滑动，则 slideToggle() 可向下滑动它们。

可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是滑动完成后所执行的函数名称。

下面的例子演示了 slideToggle() 方法：


## 实例

```text
$("#flip").click(function(){
  $("#panel").slideToggle();
});
```


## 复习重点

- 能说明 `jQuery 滑动` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
