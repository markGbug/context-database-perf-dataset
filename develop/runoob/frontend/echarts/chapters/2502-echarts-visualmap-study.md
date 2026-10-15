# ECharts：ECharts 数据的视觉映射

- 来源：[ECharts 数据的视觉映射](https://www.runoob.com/echarts/echarts-visualmap.html)
- 分类：前端开发
- 技术：ECharts
- 笔记类型：学习笔记
- 章节序号：2502

## 本章内容

数据可视化简单来讲就是将数据用图表的形式来展示，专业的表达方式就是数据到视觉元素的映射过程。

ECharts 的每种图表本身就内置了这种映射过程，我们之前学习到的柱形图就是将数据映射到长度。

此外，ECharts 还提供了 visualMap 组件 来提供通用的视觉映射。visualMap 组件中可以使用的视觉元素有：

- 图形类别（symbol）
- 图形大小（symbolSize）
- 颜色（color）
- 透明度（opacity）
- 颜色透明度（colorAlpha）
- 颜色明暗度（colorLightness）
- 颜色饱和度（colorSaturation）
- 色调（colorHue）


## 数据和维度

ECharts 中的数据，一般存放于 series.data 中。

不同的图表类型，数据格式有所不一样，但是他们的共同特点就都是数据项（dataItem） 的集合。每个数据项含有 数据值（value） 和其他信息（可选）。每个数据值，可以是单一的数值（一维）或者一个数组（多维）。

series.data 最常见的形式 是线性表，即一个普通数组：

在图表中，往往默认把 value 的前一两个维度进行映射，比如取第一个维度映射到x轴，取第二个维度映射到y轴。如果想要把更多的维度展现出来，可以借助 visualMap 。


## visualMap 组件

visualMap 组件定义了把数据的指定维度映射到对应的视觉元素上。

visualMap 组件可以定义多个，从而可以同时对数据中的多个维度进行视觉映射。

visualMap 组件可以定义为 分段型（visualMapPiecewise） 或 连续型（visualMapContinuous），通过 type 来区分。例如：

分段型视觉映射组件，有三种模式：

- 连续型数据平均分段: 依据 visualMap-piecewise.splitNumber 来自动平均分割成若干块。
- 连续型数据自定义分段: 依据 visualMap-piecewise.pieces 来定义每块范围。
- 离散数据根据类别分段: 类别定义在 visualMap-piecewise.categories 中。

分段型视觉映射组件，展现形式如下图：


## 实例


## 视觉映射方式的配置

visualMap 中可以指定数据的指定维度映射到对应的视觉元素上。


## 实例 1


## 实例 2

更多详情，参见 visualMap.inRange 和 visualMap.outOfRange。


## 复习重点

- 能说明 `ECharts 数据的视觉映射` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
