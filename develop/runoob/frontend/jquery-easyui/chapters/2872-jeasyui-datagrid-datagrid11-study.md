# jQuery EasyUI：jQuery EasyUI 数据网格 - 自定义分页

- 来源：[jEasyUI 自定义分页](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid11.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：学习笔记
- 章节序号：2872

## 本章内容

数据网格（datagrid）内置一个很好特性的分页功能，自定义也相当简单。在本教程中，我们将创建一个数据网格（datagrid），并在分页工具栏上添加一些自定义按钮。

```html
    <table id="tt" title="Load Data" class="easyui-datagrid" style="width:550px;height:250px"
            url="data/datagrid_data.json"
            iconCls="icon-save" pagination="true">
        <thead>
            <tr>
                <th field="itemid" width="80">Item ID</th>
                <th field="productid" width="80">Product ID</th>
                <th field="listprice" width="80" align="right">List Price</th>
                <th field="unitcost" width="80" align="right">Unit Cost</th>
                <th field="attr1" width="100">Attribute</th>
                <th field="status" width="60" align="center">Stauts</th>
            </tr>
        </thead>
    </table>
```

请记得，设置 'pagination' 属性为 true，这样才会生成分页工具栏。

```javascript
    var pager = $('#tt').datagrid('getPager');    // get the pager of datagrid
    pager.pagination({
        showPageList:false,
        buttons:[{
            iconCls:'icon-search',
            handler:function(){
                alert('search');
            }
        },{
            iconCls:'icon-add',
            handler:function(){
                alert('add');
            }
        },{
            iconCls:'icon-edit',
            handler:function(){
                alert('edit');
            }
        }],
        onBeforeRefresh:function(){
            alert('before refresh');
            return true;
        }
    });
```

正如您所看到的，我们首先得到数据网格（datagrid）的 pager 对象，然后重新创建分页（pagination）。我们隐藏页面列表，并添加三个新的按钮。


## 下载 jQuery EasyUI 实例

jeasyui-datagrid-datagrid11.zip


## 复习重点

- 能说明 `jEasyUI 自定义分页` 解决什么问题。
- 能复述本章主要语法或操作步骤。
- 能根据示例推导输出结果。
- 能指出至少一个容易踩坑的地方。
