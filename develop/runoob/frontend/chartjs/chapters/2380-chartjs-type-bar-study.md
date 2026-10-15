# Chart.js：Chart.js 柱形图

- 来源：[Chart.js 柱形图](https://www.runoob.com/chartjs/chartjs-type-bar.html)
- 分类：前端开发
- 技术：Chart.js
- 笔记类型：学习笔记
- 章节序号：2380

## 本章内容

柱形图是一种以长方形的长度为变量的统计图表。

柱形图用来比较两个或以上的价值（不同时间或者不同条件），只有一个变量，通常利用于较小的数据集分析。

柱形图的 type 属性为 bar ，type 描述了图表类型。

```javascript
const config = {
  type: 'bar',
  data: data,
  options: {
    scales: {
      y: {
        beginAtZero: true
      }
    }
  },
};
```

接下来我们创建一个简单的柱形图：


## 实例

以上实例输出结果为：


### 水平柱形图

水平柱形图是垂直条形图的变，常用于显示数据趋势，以及并排比较多个数据集。

设置水平柱形图需要将选项对象中的 indexAxis 属性设置为 y，indexAxis 属性的默认值为 x。


## 实例

以上实例输出结果为：


## 复习重点

- 能说明 `Chart.js 柱形图` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
