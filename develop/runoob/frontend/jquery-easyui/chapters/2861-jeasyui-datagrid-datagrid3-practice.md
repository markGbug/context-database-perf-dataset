# jQuery EasyUI：jQuery EasyUI 数据网格 - 取得选中行数据

- 来源：[jEasyUI 取得选中行数据](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid3.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2861

## 本章内容

本实例演示如何取得选中行数据。

数据网格（datagrid）组件包含两种方法来检索选中行数据：

- getSelected：取得第一个选中行数据，如果没有选中行，则返回 null，否则返回记录。
- getSelections：取得所有选中行数据，返回元素记录的数组数据。

```html
    <table id="tt" class="easyui-datagrid" style="width:600px;height:250px"
            url="data/datagrid_data.json"
            title="Load Data" iconCls="icon-save">
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
```

取得选中行数据：

```javascript
    var row = $('#tt').datagrid('getSelected');
    if (row){
        alert('Item ID:'+row.itemid+"\nPrice:"+row.listprice);
    }
```

取得所有选中行的 itemid：

```java
    var ids = [];
    var rows = $('#tt').datagrid('getSelections');
    for(var i=0; i<rows.length; i++){
        ids.push(rows[i].itemid);
    }
    alert(ids.join('\n'));
```


## 下载 jQuery EasyUI 实例

jeasyui-datagrid-datagrid3.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 取得选中行数据` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
