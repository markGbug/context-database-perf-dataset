# ECharts：ECharts 交互组件

- 来源：[ECharts 交互组件](https://www.runoob.com/echarts/echarts-interaction.html)
- 分类：前端开发
- 技术：ECharts
- 笔记类型：学习笔记
- 章节序号：2500

## 本章内容

ECharts 提供了很多交互组件：例组件 legend、标题组件 title、视觉映射组件 visualMap、数据区域缩放组件 dataZoom、时间线组件 timeline。

接下来的内容我们将介绍如何使用数据区域缩放组件 dataZoom。


### dataZoom

dataZoom 组件可以实现通过鼠标滚轮滚动，放大缩小图表的功能。

默认情况下 dataZoom 控制 x 轴，即对 x 轴进行数据窗口缩放和数据窗口平移操作。


## 实例

上面的实例只能拖动 dataZoom 组件来缩小或放大图表。如果想在坐标系内进行拖动，以及用鼠标滚轮（或移动触屏上的两指滑动）进行缩放，那么需要 再再加上一个 inside 型的 dataZoom 组件。

在以上实例基础上我们再增加 type: 'inside' 的配置信息：


## 实例

当然我们可以通过 dataZoom.xAxisIndex 或 dataZoom.yAxisIndex 来指定 dataZoom 控制哪个或哪些数轴。


## 实例


## 复习重点

- 能说明 `ECharts 交互组件` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
