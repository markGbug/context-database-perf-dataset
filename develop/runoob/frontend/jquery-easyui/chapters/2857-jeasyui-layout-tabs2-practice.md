# jQuery EasyUI：jQuery EasyUI 布局 - 动态添加标签页（Tabs）

- 来源：[jEasyUI 动态添加标签页](https://www.runoob.com/jeasyui/jeasyui-layout-tabs2.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2857

## 本章内容

通过使用 jQuery EasyUI 可以很容易地添加 Tabs。您只需要调用 'add' 方法即可。

在本教程中，我们将使用 iframe 动态地添加显示在一个页面上的 Tabs。 当点击添加按钮，一个新的 tab 将被添加。如果 tab 已经存在，它将被激活。

```html
    <div style="margin-bottom:10px">
        <a href="#" class="easyui-linkbutton" onclick="addTab('google','http://www.google.com')">google</a>
        <a href="#" class="easyui-linkbutton" onclick="addTab('jquery','http://jquery.com/')">jquery</a>
        <a href="#" class="easyui-linkbutton" onclick="addTab('easyui','http://jeasyui.com/')">easyui</a>
    </div>
    <div id="tt" class="easyui-tabs" style="width:400px;height:250px;">
        <div title="Home">
        </div>
    </div>
```

这个 html 代码非常简单,我们创建了带有一个名为 'Home' 的 tab 面板的 Tabs。请注意，我们不需要写任何的 js 代码。

```html
    function addTab(title, url){
        if ($('#tt').tabs('exists', title)){
            $('#tt').tabs('select', title);
        } else {
            var content = '<iframe scrolling="auto" frameborder="0"  src="'+url+'" style="width:100%;height:100%;"></iframe>';
            $('#tt').tabs('add',{
                title:title,
                content:content,
                closable:true
            });
        }
    }
```

我们使用 'exists' 方法来判断 tab 是否已经存在，如果已存在则激活 tab。如果不存在则调用 'add' 方法来添加一个新的 tab 面板。


## 下载 jQuery EasyUI 实例

jeasyui-layout-tabs2.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 动态添加标签页` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
