# Foundation：Foundation 网格 - 中型设备

- 来源：[Foundation 网格 - 中型设备](https://www.runoob.com/foundation/foundation-grid-medium.html)
- 分类：前端开发
- 技术：Foundation
- 笔记类型：练习笔记
- 章节序号：2555

## 本章内容

上一章节我们介绍了小型设备上我们使用 .small-* 类来设置，网格比例为 25%/75%：

```html
<div class="small-3 columns">....</div>
<div class="small-9 columns">....</div>
```

在中型设备上我们推荐的比例为 50%/50%。

提示: 中型设备的屏幕尺寸定义在 40.0625em 到 64.0624em 之间。

中型设备上使用 .medium-* 类。

现在我们在中型设备上添加两列：

```html
<div class="small-3 medium-6 columns">....</div>
<div class="small-9 medium-6 columns">....</div>
```

以上实例设置了两个列，比例为 25% 和 75% (Foundation 是移动优先: 如果没有特别说明，在大型设备上会继承 .small 类的代码):

小型设备上使用的比例为 25%/75% (.small-3 和 .small-9)。但在中型设备上使用的比例为 50%/50% (.medium-6 和 .medium-6) 。


### 实例


## 仅在中型设备上使用

以下实例中我们指定了 .medium-6 类 (不是 .small-*)。这表明在中型或大型设备上比例为 50%/50%。但在小型设备上会水平堆叠 (100% 宽度):


### 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Foundation 网格 - 中型设备` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
