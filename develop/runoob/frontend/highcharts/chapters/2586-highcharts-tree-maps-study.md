# Highcharts：Highcharts 树状图(Treemap)

- 来源：[Highcharts 树状图(Treemap)](https://www.runoob.com/highcharts/highcharts-tree-maps.html)
- 分类：前端开发
- 技术：Highcharts
- 笔记类型：学习笔记
- 章节序号：2586

## 本章内容

本章节我们将为大家介绍 Highcharts 的热点图。

我们在前面的章节已经了解了 Highcharts 配置语法。接下来让我们来看下 Highcharts 的其他配置。


## 树状图


### series 配置

设置 series 的 type 属性为 treemap ，series.type 描述了数据列类型。默认值为 "line"。

```javascript
var chart = {
   type: 'treemap'
};
```


### 实例

文件名：highcharts_tree_map.htm

```html
<html>
<head>
<meta charset="UTF-8" />
<title>Highcharts 教程 | 菜鸟教程(runoob.com)</title>
<script src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="http://code.highcharts.com/highcharts.js"></script>
<script src="http://code.highcharts.com/modules/treemap.js"></script>
<script src="http://code.highcharts.com/modules/heatmap.js"></script>
</head>
<body>
<div id="container" style="width: 550px; height: 400px; margin: 0 auto"></div>
<script language="JavaScript">
$(document).ready(function() {
   var title = {
      text: 'Highcharts Treemap'
   };

   var colorAxis = {
      minColor: '#FFFFFF',
      maxColor: Highcharts.getOptions().colors[0]
   };

   var series= [{
     type: "treemap",
     layoutAlgorithm: 'squarified',
     data: [{
        name: 'A',
        value: 6,
        colorValue: 1
     }, {
        name: 'B',
        value: 6,
        colorValue: 2
     }, {
        name: 'C',
        value: 4,
        colorValue: 3
     }, {
        name: 'D',
        value: 3,
        colorValue: 4
     }, {
        name: 'E',
        value: 2,
        colorValue: 5
     }, {
        name: 'F',
        value: 2,
        colorValue: 6
     }, {
        name: 'G',
        value: 1,
        colorValue: 7
     }]
   }];

   var json = {};
   json.title = title;
   json.colorAxis = colorAxis;
   json.series = series;

   $('#container').highcharts(json);
});
</script>
</body>
</html>
```

尝试一下 »

以上实例输出结果为：


## 不同等级树状图

以下实例使用不同颜色来标识不同等级的树状图。


### 实例

文件名：highcharts_tree_levels.htm（完整源码请点击实例查看）

```html
<html>
<head>
<meta charset="UTF-8" />
<title>Highcharts 教程 | 菜鸟教程(runoob.com)</title>
<script src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="http://code.highcharts.com/highcharts.js"></script>
<script src="http://code.highcharts.com/modules/treemap.js"></script>
<script src="http://code.highcharts.com/modules/heatmap.js"></script>
</head>
<body>
<div id="container" style="width: 550px; height: 400px; margin: 0 auto"></div>
<script language="JavaScript">
$(document).ready(function() {
   var title = {
      text: 'Fruit consumption'
   };

   var series = [{
      type: "treemap",
      layoutAlgorithm: 'stripes',
      alternateStartingDirection: true,
      levels: [{
         level: 1,
         layoutAlgorithm: 'sliceAndDice',
         dataLabels: {
            enabled: true,
            align: 'left',
            verticalAlign: 'top',
            style: {
               fontSize: '15px',
               fontWeight: 'bold'
            }
         }
      }],
      data: [{
         id: 'A',
         name: 'Apples',
         color: "#EC2500"
      }, {
         id:'B',
         name: 'Bananas',
         color: "#ECE100"
      }, {
         id: 'O',
         name: 'Oranges',
         color: '#EC9800'
      }, {
         name: 'Anne',
         parent: 'A',
         value: 5
      }, {
         name: 'Rick',
         parent: 'A',
         value: 3
      }, {
         name: 'Peter',
         parent: 'A',
         value: 4
      }, {
         name: 'Anne',
         parent: 'B',
         value: 4
      }, {
         name: 'Rick',
         parent: 'B',
         value: 10
      }, {
         name: 'Peter',
         parent: 'B',
         value: 1
      }, {
         name: 'Anne',
         parent: 'O',
         value: 1
      }, {
         name: 'Rick',
         parent: 'O',
         value: 3
      }, {
         name: 'Peter',
         parent: 'O',
         value: 3
      }, {
         name: 'Susanne',
         parent: 'Kiwi',
         value: 2,
         color: '#9EDE00'
      }]
   }];

   var json = {};
   json.title = title;
   json.series = series;

   $('#container').highcharts(json);
});
</script>
</body>
</html>
```

尝试一下 »

以上实例输出结果为：


## 大数据量树状图

以下实例颜色了大数据量的树状图，具体实例数据可通过点击"尝试一下"查看。

文件名：highcharts_tree_largemap.htm

```java
<html>
<head>
<meta charset="UTF-8" />
<title>Highcharts 教程 | 菜鸟教程(runoob.com)</title>
<script src="http://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js"></script>
<script src="http://code.highcharts.com/highcharts.js"></script>
<script src="http://code.highcharts.com/modules/treemap.js"></script>
<script src="http://code.highcharts.com/modules/heatmap.js"></script>
</head>
<body>
<div id="container" style="width: 550px; height: 400px; margin: 0 auto"></div>
<script language="JavaScript">
$(document).ready(function() {
//省略部分 js 代码
 var data = {……};
 var points = [],
        region_p,
        region_val,
        region_i,
        country_p,
        country_i,
        cause_p,
        cause_i,
        cause_name = [];
    cause_name['Communicable & other Group I'] = 'Communicable diseases';
    cause_name['Noncommunicable diseases'] = 'Non-communicable diseases';
    cause_name['Injuries'] = 'Injuries';
    region_i = 0;
    for (var region in data) {
        region_val = 0;
        region_p = {
            id: "id_" + region_i,
            name: region,
            color: Highcharts.getOptions().colors[region_i]
        };
        country_i = 0;
        for (var country in data[region]) {
            country_p = {
                id: region_p.id + "_" + country_i,
                name: country,
                parent: region_p.id
            };
            points.push(country_p);
            cause_i = 0;
            for (var cause in data[region][country]) {
                cause_p = {
                    id: country_p.id + "_" + cause_i,
                    name: cause_name[cause],
                    parent: country_p.id,
                    value: Math.round(+data[region][country][cause])
                };
                region_val += cause_p.value;
                points.push(cause_p);
                cause_i++;
            }
            country_i++;
        }
        region_p.value = Math.round(region_val / country_i);
        points.push(region_p);
        region_i++;
    }
   var chart = {
      renderTo: 'container'
   };

   var title = {
      text: 'Global Mortality Rate 2012, per 100 000 population'
   };

   var subtitle: {
      text: 'Click points to drill down. Source: <a href="http://apps.who.int/gho/data/node.main.12?lang=en">WHO</a>.'
   };

   var series = [{
      type: "treemap",
      layoutAlgorithm: 'squarified',
      allowDrillToNode: true,
      dataLabels: {
         enabled: false
      },
      levelIsConstant: false,
      levels: [{
         level: 1,
         dataLabels: {
            enabled: true
         },
      borderWidth: 3
      }],
      data: points
   }];

   var json = {};
   json.title = title;
   json.series = series;

   $('#container').highcharts(json);
});
</script>
</body>
</html>
```

尝试一下 »

以上实例输出结果为：


## 复习重点

- 能说明 `Highcharts 树状图(Treemap)` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
