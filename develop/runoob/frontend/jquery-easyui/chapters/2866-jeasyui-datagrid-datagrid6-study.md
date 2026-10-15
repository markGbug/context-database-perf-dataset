# jQuery EasyUI：jQuery EasyUI 数据网格 - 动态改变列

- 来源：[jEasyUI 动态改变列](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid6.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：学习笔记
- 章节序号：2866

## 本章内容

数据网格（DataGrid）列可以使用 'columns' 属性简单地定义。如果您想动态地改变列，那根本没有问题。为了改变列，您可以重新调用datagrid 方法，并传递一个新的 columns 属性。

```html
    <table id="tt" title="Frozen Columns" class="easyui-datagrid" style="width:550px;height:250px"
            url="data/datagrid_data.json"
            singleSelect="true" iconCls="icon-save">
    </table>
```

```text
    $('#tt').datagrid({
        columns:[[
            {field:'itemid',title:'Item ID',width:80},
            {field:'productid',title:'Product ID',width:80},
            {field:'attr1',title:'Attribute',width:200},
            {field:'status',title:'Status',width:80}
        ]]
    });
```

运行网页，您将看见：

可是有时候您想改变列，所以您需要写一些代码：

```text
    $('#tt').datagrid({
        columns:[[
            {field:'itemid',title:'Item ID',width:80},
            {field:'productid',title:'Product ID',width:80},
            {field:'listprice',title:'List Price',width:80,align:'right'},
            {field:'unitcost',title:'Unit Cost',width:80,align:'right'},
            {field:'attr1',title:'Attribute',width:100},
            {field:'status',title:'Status',width:60}
        ]]
    });
```

请记住，我们已经定义了其他属性，比如：url、width、height 等等。我们不需要再一次定义它们，我们定义那些我们需要改变的。


## 下载 jQuery EasyUI 实例

jeasyui-datagrid-datagrid6.zip


## 复习重点

- 能说明 `jEasyUI 动态改变列` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
