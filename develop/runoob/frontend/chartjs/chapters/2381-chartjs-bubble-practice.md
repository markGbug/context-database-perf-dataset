# Chart.js：Chart.js 气泡图

- 来源：[Chart.js 气泡图](https://www.runoob.com/chartjs/chartjs-bubble.html)
- 分类：前端开发
- 技术：Chart.js
- 笔记类型：练习笔记
- 章节序号：2381

## 本章内容

气泡图用于展示三个变量之间的关系。

气泡的位置由前两个变量决定，对应的是 X 轴和 Y 轴，第三个参数为气泡的大小。

```text
{
    // X 轴对应值
    x: number,

    // Y 轴对应值
    y: number,

    // 气泡半径，单位为像素
    r: number
}
```

泡图的 type 属性为 bubble ，type 描述了图表类型。

```javascript
const config = {
  type: 'bubble',
  data: data,
  options: {}
};
```

接下来我们创建一个简单的气泡图：


## 实例

以上实例输出结果为：


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `Chart.js 气泡图` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
