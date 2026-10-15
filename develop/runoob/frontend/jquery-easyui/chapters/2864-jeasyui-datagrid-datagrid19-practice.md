# jQuery EasyUI：jQuery EasyUI 数据网格 - 创建复杂工具栏

- 来源：[jEasyUI 创建复杂工具栏](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid19.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2864

## 本章内容

数据网格（datagrid）的工具栏（toolbar）可以包含按钮及其他组件。 您可以通个一个已存在的 DIV 标签来简单地定义工具栏布局，该 DIV 标签将成为数据网格（datagrid）工具栏的内容。 本教程将向您展示如何创建数据网格（datagrid）组件的复杂工具栏。

```html
    <div id="tb" style="padding:5px;height:auto">
        <div style="margin-bottom:5px">
            <a href="#" class="easyui-linkbutton" iconCls="icon-add" plain="true"></a>
            <a href="#" class="easyui-linkbutton" iconCls="icon-edit" plain="true"></a>
            <a href="#" class="easyui-linkbutton" iconCls="icon-save" plain="true"></a>
            <a href="#" class="easyui-linkbutton" iconCls="icon-cut" plain="true"></a>
            <a href="#" class="easyui-linkbutton" iconCls="icon-remove" plain="true"></a>
        </div>
        <div>
            Date From: <input class="easyui-datebox" style="width:80px">
            To: <input class="easyui-datebox" style="width:80px">
            Language:
            <input class="easyui-combobox" style="width:100px"
                    url="data/combobox_data.json"
                    valueField="id" textField="text">
            <a href="#" class="easyui-linkbutton" iconCls="icon-search">Search</a>
        </div>
    </div>
```

```html
    <table class="easyui-datagrid" style="width:600px;height:250px"
            url="data/datagrid_data.json"
            title="DataGrid - Complex Toolbar" toolbar="#tb"
            singleSelect="true" fitColumns="true">
        <thead>
            <tr>
                <th field="itemid" width="60">Item ID</th>
                <th field="productid" width="80">Product ID</th>
                <th field="listprice" align="right" width="70">List Price</th>
                <th field="unitcost" align="right" width="70">Unit Cost</th>
                <th field="attr1" width="200">Address</th>
                <th field="status" width="50">Status</th>
            </tr>
        </thead>
    </table>
```

正如您所看到的，数据网格（datagrid）的工具栏域对话框（dialog）相似。我们不需要写任何的 javascript 代码，就能创建带有复杂工具栏的数据网格（datagrid）。


## 下载 jQuery EasyUI 实例

jeasyui-datagrid-datagrid19.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 创建复杂工具栏` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
