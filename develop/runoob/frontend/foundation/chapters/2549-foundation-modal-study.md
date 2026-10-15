# Foundation：Foundation 模态框

- 来源：[Foundation 模态框](https://www.runoob.com/foundation/foundation-modal.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：学习笔记
- 章节序号：2549

## 本章内容

模态框是一个显示在页面头部的弹窗。

我们可以在容器元素上(如 <div id="myModal")使用唯一 ID，并添加 .reveal-modal 类和 data-reveal 属性来添加模态框。我们可以在任何元素上使用 data-reveal-id="id" 属性阿里打开模态框。 id 必须与容器 id 一致(实例为 "myModal")。

如果你希望在点击模态框之外的区域来关闭模态框。你可以在模态框的关闭按钮 <a> 标签上添加 .close-reveal-modal 类来实现。

注意: 滑块需要使用 JavaScript。所以你需要初始化 Foundation JS:


### 实例


## 模态框大小

可以在模态框容器上添加以下类来设置模态框的大小：

- .tiny: 30% 宽度
- .small: 40% 宽度
- .medium: 60% 宽度
- .large: 70% 宽度
- .xlarge: 95% 宽度
- .full: 100% 宽度和高度

注意: 在平板、笔记本、PC 电脑上默认为 80% 宽度，在小屏幕设备上是 100% 宽度。


### 实例


## 内嵌模态框

你可以在模态框内嵌入模态框，可以在第一个模态框上添加新的触发按钮。你必须为内嵌模态框设置一个唯一的 id：


### 实例

第二个模态框会取代第一个模态框。如果你希望在打开第二个模态框时，不关闭第一个模态框。可以在第二个模态框上添加 data-options="multiple_opened:true;" 属性：


### 实例


## 复习重点

- 能说明 `Foundation 模态框` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
