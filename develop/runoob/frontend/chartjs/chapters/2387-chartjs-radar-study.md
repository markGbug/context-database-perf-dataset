# Chart.js：Chart.js 雷达图

- 来源：[Chart.js 雷达图](https://www.runoob.com/chartjs/chartjs-radar.html)
- 分类：前端开发
- 技术：Chart.js
- 笔记类型：学习笔记
- 章节序号：2387

## 本章内容

雷达图是一种显示多个数据点及其之间变化的方式。

雷达图是以从同一点开始的轴上表示的三个或更多个定量变量的二维图表的形式显示多变量数据的图形方法。

轴的相对位置和角度通常是无信息的。

混合图 type 属性为 radar。

```javascript
const config = {
  type: 'radar',
  data: data,
  options: {
    elements: {
      line: {
        borderWidth: 3 // 设置线条宽度
      }
    }
  },
};
```

接下来我们创建一个简单的雷达图：


## 实例

以上实例输出结果为：


## 复习重点

- 能说明 `Chart.js 雷达图` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
