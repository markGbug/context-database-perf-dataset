# ECharts：ECharts 旭日图

- 来源：[ECharts 旭日图](https://www.runoob.com/echarts/echarts-sunburst.html)
- 分类：前端开发
- 技术：ECharts
- 笔记类型：练习笔记
- 章节序号：2504

## 本章内容

旭日图（Sunburst）由多层的环形图组成，在数据结构上，内圈是外圈的父节点。因此，它既能像饼图一样表现局部和整体的占比，又能像矩形树图一样表现层级关系。

ECharts 创建旭日图很简单，只需要在 series 配置项中声明类型为 sunburst 即可，data 数据结构以树形结构声明，看下一个简单的实例：


## 实例


## 颜色等样式调整

默认情况下会使用全局调色盘 color 分配最内层的颜色，其余层则与其父元素同色。

在旭日图中，扇形块的颜色有以下三种设置方式：

- 在 series.data.itemStyle 中设置每个扇形块的样式。
- 在 series.levels.itemStyle 中设置每一层的样式。
- 在 series.itemStyle 中设置整个旭日图的样式。

上述三者的优先级是从高到低的，也就是说，配置了 series.data.itemStyle 的扇形块将会覆盖 series.levels.itemStyle 和 series.itemStyle 的设置。

下面，我们将整体的颜色设为灰色 #aaa，将最内层的颜色设为蓝色 blue，将 Aa、B 这两块设为红色 red。


## 实例

按层配置样式是一个很常用的功能，能够很大程度上提高配置的效率。


## 数据下钻

旭日图默认支持数据下钻，也就是说，当点击了扇形块之后，将以该扇形块的数据作为根节点，进一步显示该数据的细节。

在数据下钻后，图形的中间会出现一个用于返回上一层的图形，该图形的样式可以通过 levels[0] 配置。


## 实例

如果不需要数据下钻功能，可以通过将 nodeClick 设置为 false 来关闭，也可以设为 'link'，并将 data.link 设为点击扇形块对应打开的链接。


## 高亮相关扇形块

旭日图支持鼠标移动到某扇形块时，高亮相关数据块的操作，可以通过设置 highlightPolicy，包括以下几种高亮方式：

- 'descendant'（默认值）：高亮鼠标移动所在扇形块与其后代元素；
- 'ancestor'：高亮鼠标所在扇形块与其祖先元素；
- 'self'：仅高亮鼠标所在扇形块；
- 'none'：不会淡化（downplay）其他元素。

上面提到的"高亮"，对于鼠标所在的扇形块，会使用 emphasis 样式；对于其他相关扇形块，则会使用 highlight 样式。通过这种方式，可以很方便地实现突出显示相关数据的需求。

具体来说，对于配置项：

```text
itemStyle: {
    color: 'yellow',
    borderWidth: 2,
    emphasis: {
        color: 'red'
    },
    highlight: {
        color: 'orange'
    },
    downplay: {
        color: '#ccc'
    }
}
```

highlightPolicy 为 'descendant':


## 实例

highlightPolicy 为 'ancestor' :


## 实例


## 更多实例

- 旭日图 1
- 旭日图 2

更多旭日图配置参考：https://www.echartsjs.com/zh/option.html#series-sunburst


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ECharts 旭日图` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
