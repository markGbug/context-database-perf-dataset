# Foundation：Foundation 选项卡

- 来源：[Foundation 选项卡](https://www.runoob.com/foundation/foundation-tabs.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：练习笔记
- 章节序号：2537

## 本章内容

选项卡导航可以很好的展示不同的内容，并可以对内容进行切换。

选项卡使用 <ul class="tabs" data-tab> 来创建, 各个选项使用 <li> 元素并加上 .tab-title 类来创建。

提示: 当前选中项可以使用 .active 类。


### 实例


## 垂直的选项卡

垂直选项卡可以使用 .vertical 类:


### 实例


## 切换选项卡

如果要设置切换标签，可以使用 <div> 元素加上 .content 类。每个选项卡上加上唯一的 ID, 并连接到列表项 (<a href="#menu1" 将打开 id="menu1" 的选项内容)。最后将所有的选项内容放在 <div> 元素上，该 <div> 元素需要添加 .tabs-content 类，并初始化 Foundation JS。

注意 .active 类会自动添加到当前选中的选项卡上：


### 实例


## 选项卡淡入

使用 CSS 来自定义选项卡淡入的效果：


### 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Foundation 选项卡` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
