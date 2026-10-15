# jQuery Mobile：jQuery Mobile 方向改变事件

- 来源：[jQuery Mobile 方向改变事件](https://www.runoob.com/jquerymobile/jquerymobile-events-orientation.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：学习笔记
- 章节序号：3356

## 本章内容

## jQuery Mobile 方向改变（orientationchange）事件

当用户垂直或水平旋转移动设备时，触发方向改变（orientationchange）事件。

如需使用方向改变（orientationchange）事件，请附加它到 window 对象：

```text
$(window).on("orientationchange",function(){
    alert("方向有改变!");
});
```

回调函数可有一个参数，event 对象，返回移动设备的方向："纵向"（设备保持在垂直位置）或"横向"（设备保持在水平位置）：


## 实例

由于方向改变（orientationchange）事件绑定到 window 对象，我们可以使用 window.orientation 属性来设置不同的样式，以便区分纵向和横向的视图：


## 实例


## 复习重点

- 能说明 `jQuery Mobile 方向改变事件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
