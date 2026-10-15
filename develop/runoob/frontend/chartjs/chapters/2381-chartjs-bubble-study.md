# Chart.js：Chart.js 气泡图

- 来源：[Chart.js 气泡图](https://www.runoob.com/chartjs/chartjs-bubble.html)
- 分类：前端开发
- 技术：Chart.js
- 笔记类型：学习笔记
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


## 复习重点

- 能说明 `Chart.js 气泡图` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
