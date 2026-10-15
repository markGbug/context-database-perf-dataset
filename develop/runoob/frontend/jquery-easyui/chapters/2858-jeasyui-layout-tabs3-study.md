# jQuery EasyUI：jQuery EasyUI 布局 - 添加自动播放标签页（Tabs）

- 来源：[jEasyUI 添加自动播放标签页](https://www.runoob.com/jeasyui/jeasyui-layout-tabs3.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：学习笔记
- 章节序号：2858

## 本章内容

本教程将向您展示如何创建一个自动播放的 Tabs。 Tabs 组件显示第一个 tab 面板，然后显示第二个、第三个... 我们将写一些代码来自动地切换 tab 面板，然后让它循环。

```html
    <div id="tt" class="easyui-tabs" style="width:330px;height:270px;">
        <div title="Shirt1" style="padding:20px;">
            <img src="images/shirt1.gif">
        </div>
        <div title="Shirt2" style="padding:20px;">
            <img src="images/shirt2.gif">
        </div>
        <div title="Shirt3" style="padding:20px;">
            <img src="images/shirt3.gif">
        </div>
        <div title="Shirt4" style="padding:20px;">
            <img src="images/shirt4.gif">
        </div>
        <div title="Shirt5" style="padding:20px;">
            <img src="images/shirt5.gif">
        </div>
    </div>
```

```javascript
    var index = 0;
    var t = $('#tt');
    var tabs = t.tabs('tabs');
    setInterval(function(){
        t.tabs('select', tabs[index].panel('options').title);
        index++;
        if (index >= tabs.length){
            index = 0;
        }
    }, 3000);
```

正如您所看到的，我们调用 'tabs' 方法来得到所有 tab 面板，并使用 'setInterval' 函数来切换他们。


## 下载 jQuery EasyUI 实例

jeasyui-layout-tabs3.zip


## 复习重点

- 能说明 `jEasyUI 添加自动播放标签页` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
