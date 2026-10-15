# jQuery EasyUI：jQuery EasyUI 数据网格 - 添加工具栏

- 来源：[jEasyUI 添加工具栏](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid4.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：学习笔记
- 章节序号：2863

## 本章内容

本实例演示如何添加工具栏（toolbar）到数据网格（datagrid）。

```html
    <table id="tt" class="easyui-datagrid" style="width:600px;height:250px"
            url="data/datagrid_data.json"
            title="DataGrid with Toolbar" iconCls="icon-save"
            toolbar="#tb">
        <thead>
            <tr>
                <th field="itemid" width="80">Item ID</th>
                <th field="productid" width="80">Product ID</th>
                <th field="listprice" width="80" align="right">List Price</th>
                <th field="unitcost" width="80" align="right">Unit Cost</th>
                <th field="attr1" width="150">Attribute</th>
                <th field="status" width="60" align="center">Stauts</th>
            </tr>
        </thead>
    </table>
    <div id="tb">
        <a href="#" class="easyui-linkbutton" iconCls="icon-add" plain="true" onclick="javascript:alert('Add')">Add</a>
        <a href="#" class="easyui-linkbutton" iconCls="icon-cut" plain="true" onclick="javascript:alert('Cut')">Cut</a>
        <a href="#" class="easyui-linkbutton" iconCls="icon-save" plain="true" onclick="javascript:alert('Save')">Save</a>
    </div>
```

我们不需要写任何的 javascript 代码，只需通过 'toolbar' 属性附加工具栏（toolbar）到数据网格（datagrid）。


## 下载 jQuery EasyUI 实例

jeasyui-datagrid-datagrid4.zip


## 复习重点

- 能说明 `jEasyUI 添加工具栏` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
