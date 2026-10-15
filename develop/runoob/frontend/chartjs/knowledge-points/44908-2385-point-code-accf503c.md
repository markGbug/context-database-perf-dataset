# 知识点 44908：Chart.js：Chart.js 混合图 - 本章内容

- 来源：[Chart.js 混合图](https://www.runoob.com/chartjs/chartjs-scatter.html)
- 来源章节：[2385-chartjs-scatter-practice.md](../chapters/2385-chartjs-scatter-practice.md)
- 分类：前端开发
- 技术：Chart.js
- 所在小节：本章内容
- 知识类型：代码
- 原章节序号：2385

## 原文片段

```text
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

## 学习理解

这段内容需要重点关注输入、执行步骤和输出结果。复习时不要只看代码表面，要说明每一行在完成什么动作。

- 先识别代码使用的语法、命令或 API。
- 再说明关键变量、参数或标签的含义。
- 最后根据代码推导运行结果或页面效果。

## 复习问题

- `本章内容` 这一小节和 `Chart.js 混合图` 的主线有什么关系？
- 如果只保留一个关键词，应该保留哪个？
- 这个知识点适合通过代码、命令、图示还是文字例子来验证？
