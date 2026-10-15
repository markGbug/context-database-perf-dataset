# Foundation：Foundation 滑块

- 来源：[Foundation 滑块](https://www.runoob.com/foundation/foundation-sliders.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：练习笔记
- 章节序号：2547

## 本章内容

Foundation 滑块允许用户通过拖动来选取区间值:

滑块可以通过使用 <div class="range-slider" data-slider> 创建。在 <div> 内, 添加两个 <span> 元素: <span class="range-slider-handle"> 创建矩形滑块（蓝色背景）， <span class="range-slider-active-segment"> 是在滑块后的灰色横条，是滑块拖动区域。

注意: 滑块需要使用 JavaScript。所以你需要初始化 Foundation JS:


### 实例


## 圆角和禁用滑块

使用 .radius 和 .round 类来添加圆角滑块。使用 .disabled 类来禁用滑块：


### 实例


## 垂直滑块

使用 .vertical-range 类和 data-options="vertical: true;" 来创建垂直滑块:


### 实例


## 滑块值

默认情况下，滑块放在横条的中间 (数值为 "50")。可以通过添加 data-options="initial: num" 属性来修改默认值:


### 实例


### 显示滑块值

如果我们需要在滑块拖动时实时显示值，可以通过在 <div> 中添加 data-options="display_selector:#id" 属性且元素 id 值与滑块的 id 匹配，如下实例：


### 实例


### 组合数据选项

以下实例使用了 display_selector 和 initial 数据选项:


### 实例


### 步长

默认情况下，滑块滑动的增加减少的数量为 "1"。可以通过添加 data-options="step: num;" 属性来修改步长值。实例中设置为 25:


### 实例


### 自定义区间

默认情况下，区间值在 "0" 到 "100"。可以通过添加 data-options start 和 end 来设置区间值。以下实例设置区间值为 "1" 到 "20":


### 实例


### 使用网格

以下使用为在网格中使用滑块：


### 实例


### 使用 Input

以下实例使用 <input> 取代 <span> 来显示滑块的值:


### 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Foundation 滑块` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
