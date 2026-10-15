# jQuery EasyUI：jQuery EasyUI 数据网格 - 添加复选框

- 来源：[jEasyUI 添加复选框](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid10.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2871

## 本章内容

本实例演示如何放置一个复选框列到数据网格（DataGrid）。通过复选框，用户将可以选择 选中/取消选中 网格行数据。

为了添加一个复选框列，我们仅仅需要添加一个列的 checkbox 属性，并设置它为 true。代码如下所示：

```html
    <table id="tt" title="Checkbox Select" class="easyui-datagrid" style="width:550px;height:250px"
            url="data/datagrid_data.json"
            idField="itemid" pagination="true"
            iconCls="icon-save">
        <thead>
            <tr>
                <th field="ck" checkbox="true"></th>
                <th field="itemid" width="80">Item ID</th>
                <th field="productid" width="80">Product ID</th>
                <th field="listprice" width="80" align="right">List Price</th>
                <th field="unitcost" width="80" align="right">Unit Cost</th>
                <th field="attr1" width="100">Attribute</th>
                <th field="status" width="60" align="center">Status</th>
            </tr>
        </thead>
    </table>
```

以上代码添加了一个带有 checkbox 属性的列，所以它将成为复选框列。如果 idField 属性已设置，数据网格（DataGrid）的选择集合将在不同的页面保持。


## 下载 jQuery EasyUI 实例

jeasyui-datagrid-datagrid10.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 添加复选框` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
