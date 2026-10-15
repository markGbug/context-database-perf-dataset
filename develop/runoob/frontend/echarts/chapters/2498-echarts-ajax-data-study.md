# ECharts：ECharts 异步加载数据

- 来源：[ECharts 异步加载数据](https://www.runoob.com/echarts/echarts-ajax-data.html)
- 分类：前端开发
- 技术：ECharts
- 笔记类型：学习笔记
- 章节序号：2498

## 本章内容

ECharts 通常数据设置在 setOption 中，如果我们需要异步加载数据，可以配合 jQuery等工具，在异步获取数据后通过 setOption 填入数据和配置项就行。


## echarts_test_data.json 数据：


## 实例

如果异步加载需要一段时间，我们可以添加 loading 效果，ECharts 默认有提供了一个简单的加载动画。只需要调用 showLoading 方法显示。数据加载完成后再调用 hideLoading 方法隐藏加载动画：


## 实例


### 数据的动态更新

ECharts 由数据驱动，数据的改变驱动图表展现的改变，因此动态数据的实现也变得异常简单。

所有数据的更新都通过 setOption 实现，你只需要定时获取数据，setOption 填入数据，而不用考虑数据到底产生了那些变化，ECharts 会找到两组数据之间的差异然后通过合适的动画去表现数据的变化。


## 实例


## 复习重点

- 能说明 `ECharts 异步加载数据` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
