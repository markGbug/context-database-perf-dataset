# Foundation：Foundation 网格 - 大型设备

- 来源：[Foundation 网格 - 大型设备](https://www.runoob.com/foundation/foundation-grid-large.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：练习笔记
- 章节序号：2556

## 本章内容

上一章节我们介绍了中型设备和小型设备的网格布局，小型设备上使用的比例为 25%/75% (.small-3 和 .small-9)，但在中型设备上使用的比例为 50%/50% (.medium-6 和 .medium-6)：

```html
<div class="small-3 medium-6 columns">....</div>
<div class="small-9 medium-6 columns">....</div>
```

在大型设备上我们推荐的比例为 33%/66%。

提示: 大型设备的屏幕尺寸定义大于 64.0625em。

大型设备上使用 .large-* 类。

现在我们在大型设备上添加两列：

```html
<div class="small-3 medium-6 large-4 columns">....</div>
<div class="small-9 medium-6 large-8 columns">....</div>
```


### 解析

- 小型设备两个列的比例为 25%/75% (.small-3 和 .small-9)
- 中型设备两个列的比例为 50%/50% (.medium-6 和 .medium-6)
- 大型设备两个列的比例为 33%/66% (.large-4 和 .large-8)


### 实例


## 仅在大型设备上使用

以下实例中我们指定了 .large-6 类 (不是 .medium-* 和 .small-*)。这表明在大型设备上比例为 50%/50%。但在中型或小型设备上会水平堆叠 (100% 宽度):


### 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Foundation 网格 - 大型设备` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
