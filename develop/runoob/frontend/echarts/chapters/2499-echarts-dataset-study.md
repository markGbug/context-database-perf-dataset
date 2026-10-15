# ECharts：ECharts 数据集（dataset）

- 来源：[ECharts 数据集（dataset）](https://www.runoob.com/echarts/echarts-dataset.html)
- 分类：前端开发
- 技术：ECharts
- 笔记类型：学习笔记
- 章节序号：2499

## 本章内容

ECharts 使用 dataset 管理数据。

dataset 组件用于单独的数据集声明，从而数据可以单独管理，被多个组件复用，并且可以基于数据指定数据到视觉的映射。

下面是一个最简单的 dataset 的例子：


## 实例

或者也可以使用常见的对象数组的格式：


## 实例


### 数据到图形的映射

我们可以在配置项中将数据映射到图形中。

我们可以使用 series.seriesLayoutBy 属性来配置 dataset 是列（column）还是行（row）映射为图形系列（series），默认是按照列（column）来映射。

以下实例我们将通过 seriesLayoutBy 属性来配置数据是使用列显示还是按行显示。


## 实例

常用图表所描述的数据大部分是"二维表"结构，我们可以使用 series.encode 属性将对应的数据映射到坐标轴（如 X、Y 轴）：


## 实例

encode 声明的基本结构如下，其中冒号左边是坐标系、标签等特定名称，如 'x', 'y', 'tooltip' 等，冒号右边是数据中的维度名（string 格式）或者维度的序号（number 格式，从 0 开始计数），可以指定一个或多个维度（使用数组）。通常情况下，下面各种信息不需要所有的都写，按需写即可。

下面是 encode 支持的属性：

```text
// 在任何坐标系和系列中，都支持：
encode: {
    // 使用 “名为 product 的维度” 和 “名为 score 的维度” 的值在 tooltip 中显示
    tooltip: ['product', 'score']
    // 使用 “维度 1” 和 “维度 3” 的维度名连起来作为系列名。（有时候名字比较长，这可以避免在 series.name 重复输入这些名字）
    seriesName: [1, 3],
    // 表示使用 “维度2” 中的值作为 id。这在使用 setOption 动态更新数据时有用处，可以使新老数据用 id 对应起来，从而能够产生合适的数据更新动画。
    itemId: 2,
    // 指定数据项的名称使用 “维度3” 在饼图等图表中有用，可以使这个名字显示在图例（legend）中。
    itemName: 3
}

// 直角坐标系（grid/cartesian）特有的属性：
encode: {
    // 把 “维度1”、“维度5”、“名为 score 的维度” 映射到 X 轴：
    x: [1, 5, 'score'],
    // 把“维度0”映射到 Y 轴。
    y: 0
}

// 单轴（singleAxis）特有的属性：
encode: {
    single: 3
}

// 极坐标系（polar）特有的属性：
encode: {
    radius: 3,
    angle: 2
}

// 地理坐标系（geo）特有的属性：
encode: {
    lng: 3,
    lat: 2
}

// 对于一些没有坐标系的图表，例如饼图、漏斗图等，可以是：
encode: {
    value: 3
}
```

更多 encode 实例：


## 实例


### 视觉通道（颜色、尺寸等）的映射

我们可以使用 visualMap 组件进行视觉通道的映射。

视觉元素可以是：

- symbol: 图元的图形类别。
- symbolSize: 图元的大小。
- color: 图元的颜色。
- colorAlpha: 图元的颜色的透明度。
- opacity: 图元以及其附属物（如文字标签）的透明度。
- colorLightness: 颜色的明暗度。
- colorSaturation: 颜色的饱和度。
- colorHue: 颜色的色调。

visualMap 组件可以定义多个，从而可以同时对数据中的多个维度进行视觉映射。


## 实例


### 交互联动

以下实例多个图表共享一个 dataset，并带有联动交互：


## 实例


## 复习重点

- 能说明 `ECharts 数据集（dataset）` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
