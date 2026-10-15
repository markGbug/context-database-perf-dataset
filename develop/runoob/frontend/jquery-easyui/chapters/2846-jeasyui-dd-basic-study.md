# jQuery EasyUI：jQuery EasyUI 拖放 - 基本的拖动和放置

- 来源：[jEasyUI 基本的拖动和放置](https://www.runoob.com/jeasyui/jeasyui-dd-basic.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：学习笔记
- 章节序号：2846

## 本章内容

本教程向您展示如何使 HTML 元素可拖动，在本例中，我们将创建三个 DIV 元素然后启用他们的拖动和放置。

首先，我们创建三个 <div> 元素：

```html
    <div id="dd1" class="dd-demo"></div>
    <div id="dd2" class="dd-demo"></div>
    <div id="dd3" class="dd-demo"></div>
```

对于第一个 <div> 元素，我们通过默认值让其可以拖动。

```text
    $('#dd1').draggable();
```

对于第二个 <div> 元素，我们通过创建一个克隆（clone）了原来元素的代理（proxy）让其可以拖动。

```text
    $('#dd2').draggable({
        proxy:'clone'
    });
```

对于第三个 <div> 元素，我们通过创建自定义代理（proxy）让其可以拖动。

```html
    $('#dd3').draggable({
        proxy:function(source){
            var p = $('<div class="proxy">proxy</div>');
            p.appendTo('body');
            return p;
        }
    });
```


## 下载 jQuery EasyUI 实例

jeasyui-dd-basic.zip


## 复习重点

- 能说明 `jEasyUI 基本的拖动和放置` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
