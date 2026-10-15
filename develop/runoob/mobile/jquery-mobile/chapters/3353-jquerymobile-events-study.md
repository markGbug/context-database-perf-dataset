# jQuery Mobile：jQuery Mobile 事件

- 来源：[jQuery Mobile 事件](https://www.runoob.com/jquerymobile/jquerymobile-events.html)
- 分类：移动开发
- 技术：jQuery Mobile
- 笔记类型：学习笔记
- 章节序号：3353

## 本章内容

事件 = 所有不同访问者访问页面的响应动作。


## jQuery Mobile 事件

在jQuery Mobile你可以使用任何标准的 jQuery 事件 。

除此之外, jQuery Mobile 也提供了针对移动端浏览器的事件：

- 触摸事件 - 当用户触摸屏幕时触发
- 滑动事件 - 当用户上下滑动时触发
- 定位事件 - 当设备水平或垂直翻转时触发
- 页面事件 - 当页面显示，隐藏，创建，加载或未加载时触发


## 初始化 jQuery Mobile 事件

在学习jQuery时我们学到了用$(document).ready()来使你的jQuery代码脚本在DOM元素加载完成后才开始执行：


## jQuery document ready 事件

但是，在 jQuery Mobile 中, 使用pageinit 事件来设置代码脚本在DOM元素加载完成后开始执行，所以要在任何新页面加载并创建是执行脚本，就需要绑定pageinit事件。

第二个参数 ("#pageone")为指定事件的页面id：


## jQuery Mobile pagecreate 事件

下一章节我们将更详细介绍 jQuery Mobile 事件。


## 复习重点

- 能说明 `jQuery Mobile 事件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
