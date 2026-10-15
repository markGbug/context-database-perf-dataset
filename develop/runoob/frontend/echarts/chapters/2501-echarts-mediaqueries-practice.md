# ECharts：ECharts 响应式

- 来源：[ECharts 响应式](https://www.runoob.com/echarts/echarts-mediaqueries.html)
- 分类：前端开发
- 技术：ECharts
- 笔记类型：练习笔记
- 章节序号：2501

## 本章内容

ECharts 图表显示在用户指定高宽的 DOM 节点（容器）中。

有时候我们希望在 PC 和 移动设备上都能够很好的展示图表的内容，实现响应式的设计，为了解决这个问题，ECharts 完善了组件的定位设置，并且实现了类似 CSS Media Query 的自适应能力。


## ECharts 组件的定位和布局

大部分『组件』和『系列』会遵循两种定位方式。


### left/right/top/bottom/width/height 定位方式

这六个量中，每个量都可以是『绝对值』或者『百分比』或者『位置描述』。

- 绝对值 单位是浏览器像素（px），用 number 形式书写（不写单位）。例如 {left: 23, height: 400}。
- 百分比 表示占 DOM 容器高宽的百分之多少，用 string 形式书写。例如 {right: '30%', bottom: '40%'}。
- 位置描述 可以设置 left: 'center'，表示水平居中。 可以设置 top: 'middle'，表示垂直居中。

这六个量的概念，和 CSS 中六个量的概念类似：

- left：距离 DOM 容器左边界的距离。
- right：距离 DOM 容器右边界的距离。
- top：距离 DOM 容器上边界的距离。
- bottom：距离 DOM 容器下边界的距离。
- width：宽度。
- height：高度。

在横向，left、right、width 三个量中，只需两个量有值即可，因为任两个量可以决定组件的位置和大小，例如 left 和 right 或者 right 和 width 都可以决定组件的位置和大小。 纵向，top、bottom、height 三个量，和横向类同不赘述。


### center / radius 定位方式

- center 是一个数组，表示 [x, y]，其中，x、y可以是『绝对值』或者『百分比』，含义和前述相同。
- radius 是一个数组，表示 [内半径, 外半径]，其中，内外半径可以是『绝对值』或者『百分比』，含义和前述相同。 在自适应容器大小时，百分比设置是很有用的。


### 横向（horizontal）和纵向（vertical）

ECharts的『外观狭长』型的组件（如 legend、visualMap、dataZoom、timeline等），大多提供了『横向布局』『纵向布局』的选择。例如，在细长的移动端屏幕上，可能适合使用『纵向布局』；在PC宽屏上，可能适合使用『横向布局』。

横纵向布局的设置，一般在『组件』或者『系列』的 orient 或者 layout 配置项上，设置为 'horizontal' 或者 'vertical'。


## 实例

以下实例中我们可以可尝试拖动右下角的圆点，图表会随着屏幕尺寸变化，legend 和 系列会自动改变布局位置和方式。

实例中我们使用了 jQuery 来加载外部数据，使用时我们需要引入 jQuery 库。


## 实例

要在 option 中设置 Media Query 须遵循如下格式：

```text
option = {
    baseOption: { // 这里是基本的『原子option』。
        title: {...},
        legend: {...},
        series: [{...}, {...}, ...],
        ...
    },
    media: [ // 这里定义了 media query 的逐条规则。
        {
            query: {...},   // 这里写规则。
            option: {       // 这里写此规则满足下的option。
                legend: {...},
                ...
            }
        },
        {
            query: {...},   // 第二个规则。
            option: {       // 第二个规则对应的option。
                legend: {...},
                ...
            }
        },
        {                   // 这条里没有写规则，表示『默认』，
            option: {       // 即所有规则都不满足时，采纳这个option。
                legend: {...},
                ...
            }
        }
    ]
};
```

上面的例子中，baseOption、以及 media 每个 option 都是『原子 option』，即普通的含有各组件、系列定义的 option。而由『原子option』组合成的整个 option，我们称为『复合 option』。baseOption 是必然被使用的，此外，满足了某个 query 条件时，对应的 option 会被使用 chart.mergeOption() 来 merge 进去。


### query

每个 query 类似于这样：

```text
{
    minWidth: 200,
    maxHeight: 300,
    minAspectRatio: 1.3
}
```

现在支持三个属性：width、height、aspectRatio（长宽比）。每个属性都可以加上 min 或 max 前缀。比如，minWidth: 200 表示『大于等于200px宽度』。两个属性一起写表示『并且』，比如：{minWidth: 200, maxHeight: 300} 表示『大于等于200px宽度，并且小于等于300px高度』。


### option

media中的 option 既然是『原子 option』，理论上可以写任何 option 的配置项。但是一般我们只写跟布局定位相关的，例如截取上面例子中的一部分 query option：

```text
media: [
    ...,
    {
        query: {
            maxAspectRatio: 1           // 当长宽比小于1时。
        },
        option: {
            legend: {                   // legend 放在底部中间。
                right: 'center',
                bottom: 0,
                orient: 'horizontal'    // legend 横向布局。
            },
            series: [                   // 两个饼图左右布局。
                {
                    radius: [20, '50%'],
                    center: ['50%', '30%']
                },
                {
                    radius: [30, '50%'],
                    center: ['50%', '70%']
                }
            ]
        }
    },
    {
        query: {
            maxWidth: 500               // 当容器宽度小于 500 时。
        },
        option: {
            legend: {
                right: 10,              // legend 放置在右侧中间。
                top: '15%',
                orient: 'vertical'      // 纵向布局。
            },
            series: [                   // 两个饼图上下布局。
                {
                    radius: [20, '50%'],
                    center: ['50%', '30%']
                },
                {
                    radius: [30, '50%'],
                    center: ['50%', '75%']
                }
            ]
        }
    },
    ...
]
```


### 多个 query 被满足时的优先级

注意，可以有多个 query 同时被满足，会都被 mergeOption，定义在后的后被 merge（即优先级更高）。


### 默认 query

如果 media 中有某项不写 query，则表示『默认值』，即所有规则都不满足时，采纳这个option。


### 容器大小实时变化时的注意事项

在不少情况下，并不需要容器DOM节点任意随着拖拽变化大小，而是只是根据不同终端设置几个典型尺寸。

但是如果容器DOM节点需要能任意随着拖拽变化大小，那么目前使用时需要注意这件事：某个配置项，如果在某一个 query option 中出现，那么在其他 query option 中也必须出现，否则不能够回归到原来的状态。（left/right/top/bottom/width/height 不受这个限制。）


### 『复合 option』 中的 media 不支持 merge

以下中我们使用了 jQuery 来加载外部数据，使用时我们需要引入 jQuery 库。该实例是一个和时间轴结合的例子：


## 实例


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `ECharts 响应式` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
