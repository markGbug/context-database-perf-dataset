# Chart.js：Chart.js 散点图

- 来源：[Chart.js 散点图](https://www.runoob.com/chartjs/chartjs-scatter2.html)
- 分类：前端开发
- 技术：Chart.js
- 笔记类型：练习笔记
- 章节序号：2388

## 本章内容

散点图是由两组数据构成多个坐标点，考察坐标点的分布，判断两变量之间是否存在某种关联或总结坐标点的分布模式。

数据结构：

```text
data: [{
        x: 10,
        y: 20
    }, {
        x: 15,
        y: 10
    }]
```

散点图 type 属性为 scatter。

```javascript
const config = {
  type: 'scatter',
  data: data,
  options: {
    scales: {
      x: {
        type: 'linear',
        position: 'bottom'
      }
    }
  }
};
```

接下来我们创建一个简单的散点图：


## 实例

以上实例输出结果为：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Chart.js 散点图` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
