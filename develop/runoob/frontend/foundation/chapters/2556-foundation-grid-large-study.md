# Foundation：Foundation 网格 - 大型设备

- 来源：[Foundation 网格 - 大型设备](https://www.runoob.com/foundation/foundation-grid-large.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：学习笔记
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


## 复习重点

- 能说明 `Foundation 网格 - 大型设备` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
