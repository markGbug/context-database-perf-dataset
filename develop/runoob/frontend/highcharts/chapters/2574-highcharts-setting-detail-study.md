# Highcharts：Highcharts 配置选项详细说明

- 来源：[Highcharts 配置说明](https://www.runoob.com/highcharts/highcharts-setting-detail.html)
- 分类：前端开发
- 技术：Highcharts
- 笔记类型：学习笔记
- 章节序号：2574

## 本章内容

Highcharts 提供大量的配置选项参数，您可以轻松定制符合用户要求的图表，本章节为大家详细介绍Highcharts 配置选项使用说明：


## 参数配置(属性+事件)

- chart.events.addSeries：添加数列到图表中。
- chart.events.click：整个图表的绘图区上所发生的点击事件。
- chart.events.load：图表加载事件。
- chart.events.redraw：图表重画事件，当点击图注显示和隐藏绘图时可以触发。
- chart.events.selection：当图表曲线可选择放大时，当选择图表操作时，可以触发该事件。
- chart.height：所绘制图表的高度值。
- chart.inverted：图表中的x，y轴对换。
- chart.polar：是否为极性图表。
- chart.reflow：当窗口大小改变时，图表宽度自适应窗口大小改变。
- chart.renderTo：图表加载的位置，是页面上的一个DOM对象。
- chart.showAxes：在空白图表中，是否显示坐标轴。
- chart.type：图表的类型，默认为line，还有bar/column/pie……
- chart.width：图表绘图区的宽度，默认为自适应。
- chart.zoomType：图表中数据报表的放大类型，可以以X轴放大，或是以Y轴放大，还可以以XY轴同时放大。
- colors：图表中多数列时，各数列之间的颜色。是一个数组，一般不动。
- credits.enabled：是否允许显示版权信息。
- credits.href：版权所有的链接。
- credits.text：版权信息显示文字。
- exporting.buttons.exportButton.enabled：是否允许显示导出按钮。
- exporting.buttons.exportButton.menuItems：导出按钮的菜单选项。
- exporting.buttons.exportButton.onclick：导出按钮被点击的事件，不是内部的菜单。
- exporting.buttons.printButton.enabled：是否允许打印按钮。
- exporting.buttons.printButton.onclick：打印按钮的点击事件。
- exporting.enabled：打印和导出按钮是否被允许。
- exporting.filename：被导出文件的文件名。
- exporting.type：默认导出图片的文件格式。
- exporting.url：SVG图表转换并导出的接口处理地址。
- exporing.width：默认导出图片的宽度。


## Chart：图表区选项

Chart图表区选项用于设置图表区相关属性。


## Color：颜色选项

Color颜色选项用于设置图表的颜色方案。

Highcharts已经默认提供了多种颜色方案，当要显示的图形多于颜色种类时，多出的图形会自动从第一种颜色方案开始选取。自定义颜色方案的方法：

```text
Highcharts.setOptions({
    colors: ['#058DC7', '#50B432', '#ED561B', '#DDDF00', '#24CBE5', '#64E572', '#FF9655',
'#FFF263', '#6AF9C4']
});
```


## Title：标题选项

Title标题选项用于设置图表的标题相关属性。


## Subtitle：副标题选项

副标题提供的属性选项与标题title大致相同，可参照上述标题选项，值得一提的是副标题的text选项默认为''，即空的，所以默认情况下副标题不显示。


## xAxis：X轴选项

X轴选项用于设置图表X轴相关属性。


## yAxis：Y轴选项

Y轴选项与上述xAxis选项基本一致，请参照上表中的参数设置，不再单独列出。


## Series：数据列选项

数据列选项用于设置图表中要展示的数据相关的属性。


## plotOptions：数据点选项

plotOptions用于设置图表中的数据点相关属性。plotOptions根据各种图表类型，其属性设置略微有些差异，现将常用选项列出来。


## Tooltip：数据点提示框

Tooltip用于设置当鼠标滑向数据点时显示的提示框信息。


## Legend：图例选项

legend用于设置图例相关属性。

更多详细信息请参照highcharts官网英文文档：http://api.highcharts.com/highcharts


## 复习重点

- 能说明 `Highcharts 配置说明` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
