# jQuery EasyUI：jQuery EasyUI 数据网格 - 添加分页组件

- 来源：[jEasyUI 添加分页组件](https://www.runoob.com/jeasyui/jeasyui-datagrid-datagrid2.html)
- 分类：前端开发
- 技术：jQuery EasyUI
- 笔记类型：练习笔记
- 章节序号：2884

## 本章内容

本实例演示如何从服务器端加载数据，如何添加分页组件（pagination）到数据网格（datagrid）。

为了从远程服务器端加载数据，您应该设置 'url' 属性，在您的服务器端应该返回 JSON 格式数据。请看数据网格（datagrid）文档得到更多关于它的数据格式信息。

```html
    <table id="tt" class="easyui-datagrid" style="width:600px;height:250px"
            url="datagrid2_getdata.php"
            title="Load Data" iconCls="icon-save"
            rownumbers="true" pagination="true">
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

我们定义数据网格（datagrid）列，并设置 'pagination' 属性为 true，它将在数据网格（datagrid）的底部生成一个分页（pagination）工具栏。pagination将发送两个参数到服务器：

- page：页码，起始值 1。
- rows：每页显示行。

```java
    $page = isset($_POST['page']) ? intval($_POST['page']) : 1;
    $rows = isset($_POST['rows']) ? intval($_POST['rows']) : 10;
    // ...
    $rs = mysql_query("select count(*) from item");
    $row = mysql_fetch_row($rs);
    $result["total"] = $row[0];

    $rs = mysql_query("select * from item limit $offset,$rows");

    $items = array();
    while($row = mysql_fetch_object($rs)){
        array_push($items, $row);
    }
    $result["rows"] = $items;

    echo json_encode($result);
```


## 下载 jQuery EasyUI 实例

jeasyui-datagrid-datagrid2.zip


## 动手验证

- 跟着本章示例重新输入一遍，不要只复制粘贴 `jEasyUI 添加分页组件` 的代码。
- 修改一个条件、参数或输入值，观察输出是否符合预期。
- 记录一次出错信息，并写下定位步骤和修复方式。
- 用自己的话解释示例为什么会得到当前输出。
