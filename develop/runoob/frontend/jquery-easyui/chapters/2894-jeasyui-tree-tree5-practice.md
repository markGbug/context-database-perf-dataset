# jQuery EasyUI：jQuery EasyUI 树形菜单 - 树形菜单拖放控制

- 来源：[jEasyUI 树形菜单拖放控制](https://www.runoob.com/jeasyui/jeasyui-tree-tree5.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2894

## 本章内容

当在一个应用中使用树（Tree）插件，拖拽（drag）和放置（drop）功能要求允许用户改变节点位置。启用拖拽（drag）和放置（drop）操作，所有您需要做的就是把树（Tree）插件的 'dnd' 属性设置为 true。

```text
    $('#tt').tree({
        dnd: true,
        url: 'tree_data.json'
    });
```

当在一个树节点上发生放置操作，'onDrop' 事件将被触发，您应该做一些或更多的操作，例如保存节点状态到远程服务器端，等等。

```javascript
    onDrop: function(targetNode, source, point){
        var targetId = $(target).tree('getNode', targetNode).id;
        $.ajax({
            url: '...',
            type: 'post',
            dataType: 'json',
            data: {
                id: source.id,
                targetId: targetId,
                point: point
            }
        });
    }
```


## 下载 jQuery EasyUI 实例

jeasyui-tree-tree5.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 树形菜单拖放控制` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
