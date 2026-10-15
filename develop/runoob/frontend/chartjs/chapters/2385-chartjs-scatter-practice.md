# Chart.js：Chart.js 混合图

- 来源：[Chart.js 混合图](https://www.runoob.com/chartjs/chartjs-scatter.html)
- 分类：前端开发
- 技术：Chart.js
- 笔记类型：练习笔记
- 章节序号：2385

## 本章内容

Chart.js 可以创建由两种或多种不同图表类型组合而成的混合图表，比如条形图与折线图的混合。

创建混合图表时，我们在每个数据集上指定图表类型。

混合图 type 属性为 scatter。

柱形图 type 属性为 bar ，折线图 type 属性为 line ， type 描述了图表类型。

```javascript
const mixedChart = new Chart(ctx, {
    data: {
        datasets: [{
            type: 'bar',
            label: '柱形图数据集',
            data: [45, 49,52, 48]
        }, {
            type: 'line',
            label: '折线图数据集',
            data: [50, 40, 45, 49],
        }],
        labels: ['一月份', '二月份', '三月份', '四月份']
    },
    options: options
});
```

接下来我们创建一个简单的混合图：


## 实例

以上实例输出结果为：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Chart.js 混合图` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
