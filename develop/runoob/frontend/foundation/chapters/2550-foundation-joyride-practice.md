# Foundation：Foundation Joyride

- 来源：[Foundation Joyride](https://www.runoob.com/foundation/foundation-joyride.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：练习笔记
- 章节序号：2550

## 本章内容

Joyride 是一个功能向导的 JavaScript 效果，创建实例如下：


### 实例


### 实例解析

以上实例中，我们创建了两个元素，每个元素都有独立的 ID。 两个元素设置了 joyride 开始和结束的位置。

我们在 <ol> 或 <ul> 元素上添加 data-joyride 属性和 .joyride-list 类来创建 joyride。你需要在文档头部定义它 (在 <body> 内的头部)。在每个列表上使用 <li> 元素，每个元素添加 data-id="value" 属性。属性的 value 必须与之前元素的 id 相同。所以第一个功能导航 <h3> 元素使用 id="first" 必须与 <li> 元素的 data-id="first" 值一致。

如果你没有管理停止的 id，将显示一个模态框。

最后，Joyride 需要使用 JavaScript 初始化它，代码为： $(document).foundation('joyride', 'start');


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Foundation Joyride` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
